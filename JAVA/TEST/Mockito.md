Metoda `Mockito.mock()` tworzy obiekt typu mock na podstawie klasy albo interfejsu, jaki podamy w argumencie. Następnie możemy ustawić kiedy, jakie wartości ma ów obiekt zwracać, albo weryfikować, jakie metody zostały wykonane.

```java
@Test
    public void testGetNoRoomsWhenWrongSize() {
        
//given
        List<Room> rooms = new ArrayList<>();
        rooms.add(new Room("101", Arrays.asList(BedType.DOUBLE)));
        rooms.add(new Room("102", Arrays.asList(BedType.SINGLE)));
        rooms.add(new Room("103", Arrays.asList(BedType.DOUBLE, BedType.SINGLE)));
        
        RoomRepository roomRepository = Mockito.mock(RoomRepository.class);
        ReservationService reservationService = Mockito.mock(ReservationService.class);
        
        Mockito.when(roomRepository.findAll()).thenReturn(rooms);
        RoomService roomService = new RoomService(roomRepository, reservationService);

        //when
        List<Room> result = roomService.getRoomsForSize(-1);

        //then
        assertEquals(0, result.size());

    }
```
W ten sposób możemy tworzyć mocki zarówno na poziomie metod testowych (`testGetNoRoomsWhenWrongSize` w tym wypadku) jak i pól (stanu) całej klasy testowej.


Adnotacja `@Mock` jest używana jako skrót dla `Mockito.mock()`. Możemy jej używać tylko na poziomie pól klasy albo przy wstrzykiwaniu mocków jako parametrów metody testowej. Musimy też oznaczyć klasę testową dodatkowo adnotacją `@ExtendWith(MockitoExtension.class)`

```java
@ExtendWith(MockitoExtension.class)
public class RoomServiceTest {

    @Mock
    private RoomRepository roomRepository;
    @Mock
    private ReservationService reservationService;

    @Test
    public void testGetNoRoomsWithWrongSize() {
        //given
        List<Room> rooms = new ArrayList<>();
        rooms.add(new Room("101", Arrays.asList(BedType.DOUBLE)));
        rooms.add(new Room("102", Arrays.asList(BedType.SINGLE)));
        rooms.add(new Room("103", Arrays.asList(BedType.DOUBLE, BedType.SINGLE)));
        Mockito.when(roomRepository.findAll()).thenReturn(rooms);
        RoomService roomService = new RoomService(roomRepository, reservationService);

        //when
        List<Room> result = roomService.getRoomsForSize(4);

        //then
        assertEquals(0, result.size());

    }
}
```
W tym wypadku musimy pamiętać o resetowaniu mocków przed każdym testem. Alternatywnym, lepszym rozwiązaniem jest wstrzyknięcie ich jako parametrów do metody testującej.
Dzięki MockitoExtension będziemy informowani (za pomocą wyjątku. `UnnecessaryStubbingException`) jeśli zamockowana metoda (np. `Mockito.when(roomRepository.findAll()).thenReturn(rooms)`) jest nieużywan.

```java
@ExtendWith(MockitoExtension.class)
public class RoomServiceTest {

    @Test
    public void testGetNoRoomsWithWrongSize(@Mock RoomRepository roomRepository, @Mock ReservationService reservationService) {
        //given
        List<Room> rooms = new ArrayList<>();
        rooms.add(new Room("101", Arrays.asList(BedType.DOUBLE)));
        rooms.add(new Room("102", Arrays.asList(BedType.SINGLE)));
        rooms.add(new Room("103", Arrays.asList(BedType.DOUBLE, BedType.SINGLE)));
        Mockito.when(roomRepository.findAll()).thenReturn(rooms);
        RoomService roomService = new RoomService(roomRepository, reservationService);

        //when
        List<Room> result = roomService.getRoomsForSize(-1);

        //then
        assertEquals(0, result.size());

    }
}

```
lub z wykorzystaniem `Mockito.mock()`:
```java
public class RoomServiceTest {

    private RoomRepository roomRepository = Mockito.mock(RoomRepository.class);
    private ReservationService reservationService = Mockito.mock(ReservationService.class);

    @Test
    public void testGetNoRoomsWithWrongSize() {
        //given
        List<Room> rooms = new ArrayList<>();
        rooms.add(new Room("101", Arrays.asList(BedType.DOUBLE)));
        rooms.add(new Room("102", Arrays.asList(BedType.SINGLE)));
        rooms.add(new Room("103", Arrays.asList(BedType.DOUBLE, BedType.SINGLE)));
        Mockito.when(roomRepository.findAll()).thenReturn(rooms);
        RoomService roomService = new RoomService(roomRepository, reservationService);

        //when
        List<Room> result = roomService.getRoomsForSize(-1);

        //then
        assertEquals(0, result.size());

    }
}
```

`MockBean` używane jest tylko w frameworku Spring
w aplikacjach używających frameworka Spring możemy pisać standardowe testy jednostkowe, mockując za pomocą Mockito wszelkie komponenty (np. serwisy i repozytoria, ale też na przykład filtry) tak jak standardowe klasy (tak jak robie to w powyższych przykładach) .
Możemy też uruchamiać testy, które będą korzystać z całego kontekstu springowego, zadziała wówczas automatyczne wstrzykiwanie i inne, sprignowe „zabawki”
Adnotacja `@MockBean` jest używana przy testach kontekstowych w frameworku Spring, na poziomie pól klasy testowej.

```java
@WebMvcTest(controllers = RestRoomController.class)
@AutoConfigureMockMvc(addFilters = false)
public class RestRoomControllerTest {


    @Autowired
    private MockMvc mockMvc;

    @MockBean
    private ReservationService reservationService;

    @Autowired
    private ObjectMapper mapper;

    @WithMockUser(username = "pawelcwik", roles = {"RECEPTION"} )
    @Test
    public void getFreeRoomsHappyPath() throws Exception {

        //given

        String url = "/api/getFreeRooms?from=2022-03-12&to=2022-03-13&size=2";

        LocalDate fromDate = LocalDate.parse("2022-03-12");
        LocalDate toDate = LocalDate.parse("2022-03-13");
        int size = 2;


        Room r = new Room("101", new ArrayList<>());
        r.setId(101);

        Mockito.when(reservationService.getAvailableRooms(fromDate, toDate, size)).thenReturn(Arrays.asList(r));

        MockHttpServletRequestBuilder request = get(url);


        //when

        MvcResult result = mockMvc.perform(request).andReturn();

        //then

        MockHttpServletResponse response = result.getResponse();

        CollectionType dtoCollection = mapper.getTypeFactory().constructCollectionType(List.class, RoomAvailableDTO.class);
        List<RoomAvailableDTO> results = mapper.readValue(response.getContentAsString(), dtoCollection);

        assertTrue(response.getStatus() == HttpStatus.OK.value());
        assertTrue(response.getContentType().equals("application/json"));
        assertTrue(results.size()==1);
        assertTrue(results.get(0).getNumber().equals("101"));

        Mockito.verify(reservationService, Mockito.times(1))
                .getAvailableRooms(fromDate, toDate, size);

    }
}
```
Adnotacja `@WithMockUser` służy do ustawiania kontekstu bezpieczeństwa w jakim dany test ma zostać wykonany