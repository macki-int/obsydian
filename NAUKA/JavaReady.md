est jednostkowy powinien automatycznie testować wybrany przez Ciebie fragmentu kodu aplikacji, którego uważasz, że jest jednostką.  
  
Jednostką może być na przykład:  

1.  jedna klasa w Javie,
2.  dwie lub więcej klas, które zależą wzajemnie od siebie, ale tylko jedna z nich ma punkt wejścia dostępny na zewnątrz, który można wywołać i przetestować.
3.  cały moduł ukryty za Fasadą (jest to podobne do punktu 2.) Spoiler alert: w kolejny mailu będzie omówiona Fasada.

  
Pro Tip: Jeśli zrobisz klasę z jedną metodą publiczną, a w tej metodzie będą wywołania innych metod prywatnych, to wystarczy, że przetestujesz tę jedną metodę publiczną, ponieważ wszystkie metody prywatne zostaną przecież pokryte tym testem.  
  
Co powinny testować testy jednostkowe?  
  
Testy jednostkowe powinny testować tylko domenę aplikacji.  
  
Przykład pierwszy…  
  
Jeśli masz stronę internetową na temat ubezpieczeń samochodów, to domeną tej aplikacji może być ranking najlepszych ofert od ubezpieczycieli..  
  
W tej aplikacji to Twój autorski algorytm wybiera najlepsze ubezpieczenie i ustawia je na odpowiednim miejscu w rankingu.  
  
Robi tak na przykład rankomat.pl  
  
Jest to coś, co wyróżnia Twój biznes od innych serwisów z ubezpieczeniami i pozwala Ci na zarabianie grubych pieniędzy (np. sprzedawanie reklam na stronie z rankingiem). To jest właśnie domena tej aplikacji.  
  
I WŁAŚNIE TO MUSISZ PRZETESTOWAĆ JEDNOSTKOWO.  
  
Drugi przykład domeny, którą trzeba przetestować jednostkowo w aplikacji webowej sklepu muzycznego może być tworzenie dedykowanych playlist dla użytkowników (tak jak robi to Spotify).  
  
Proste co nie?  
  
Dla kontrastu porównajmy Test Jednostkowy i Test Integracyjny.  
  
Jeśli Twoja aplikacja komunikuje się ze zdalnym serwerem do obsługi sprzedaży ubezpieczeń po sieci (network).  
  
To na to piszę się test integracyjny.  
Taki test sprawdzi, czy zapytanie z Twojego serwisu ma poprawny format, wysyła potrzebne dane i dostaje poprawną odpowiedź. (Integracja sieci i klienta HTTP)  
  
Albo test sprawdzający, że ranking ubezpieczeń poprawnie zapisuje się do bazy danych (integracja z bazą danych).  
  
Wróćmy jednak do unit testów (testów jednostkowych).  
  
Czy musisz testować jednostkowo wszystko, co masz w aplikacji?  
  
Nie.  
  
Nie musisz mieć aplikacji pokrytej w 80% testami jednostkowymi.  
  
Nie testuj jednostkowo  

-   kodu Javy czy innych bibliotek

-   jeśli są powszechnie używane np. java.util.*
-   metody size() z java.util.List,
-   dodawania elementów metodą add() do kolekcji
-   getterow i setterów
-   mocków z Mockito.
-   Czyli takich rzeczy oczywistych, które mają działać i działają od lat by design.

-   Nie testuj Spring Boota, bo jest już przetestowany wewnątrz.
-   Operacji technicznych i niezwiązanych z domeną aplikacji

-   Aplikacja typu CRUD, która tylko wrzuca coś do bazy danych i nie ma logiki domenowej (np. Autorskiego algorytmu)
-   Zapisywanie za pomocą spring data do bazy danych przetestuj tylko integracyjnie

  
Najprościej mówiąc: testuj jednostkowo swój kod. Swoje algorytmy.  
  
Zaczynaj od testowania domeny aplikacji. Czyli miejsca w kodzie, które generuje unikalną wartość dla użytkownika tej aplikacji.

- [ ] Czego musisz się nauczyć w kontekście testów jednostkowych w Javie?  
  

1.  Przede wszystkim dobrych praktyk

1.  Testy jednostkowe powinny być super szybkie. Nie powinny one wysyłać żadnych prawdziwych zapytań po sieci czy łączyć się z bazą danych. To zabiera czas.
2.  zasady [F.I.R.S.T](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZkZXZzemN6ZXBhbmlhay5wbCUyRnRlc3R5LWplZG5vc3Rrb3dlLWZpcnN0JTJG&sig=GnVenmS6JDgdcGxtkoujR9DCapKETwnsZKfMmTVaTFwp&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1818) w testach

1.  Fast

1.  testy muszą być szybkie

3.  Isolated

1.  nie powinny od siebie zależeć

5.  Repeatable

1.  dla każdego wywołania testu rezultat powinien być ten sam. (nic z zewnątrz nie może wpływać na taki test na przykład koniec pamięci albo inny wątek, który przeszkadza)

7.  Self-validating

1.  jeśli test przechodzi to znaczy ze przechodzi i wszystko jest OK, jeśli nie przechodzi to znaczy ze nie jest OK. Nie każ innym wchodzić do kodu twojego testu i ręcznie sprawdzać, czy Twój test przeszedł

9.  Timely/Thorough

1.  oznacza, że istnieje możliwość napisania testu w dowolnym momencie historii aplikacji. Test powinien być możliwy do napisania w każdym momencie istnienia aplikacji. Czasami jest taka niepożądana sytuacja, w której nie da się napisać testów pod kod aplikacji… Patowa wręcz sytuacja. Jeśli piszesz test przed implementacją (TDD) to nie musisz się martwic ze nie będzie on możliwy do przetestowania (inaczej mówiąc testowany)

4.  Stosowania TDD
5.  Dbania o czytelność testów

1.  stosowanie AssertObject Patternu - [wpis](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZzb2Z0d2FyZXNraWxsLnBsJTJGYXNzZXJ0LW9iamVjdC1wYXR0ZXJuLXd5cmF6LXctdGVzdGFjaC1iaXpuZXNvd2Utem5hY3plbmllLW9iaWVrdHU=&sig=GA3cpvg5W65xpFttqHEFUfbywRVTSpV1LhDAsTFPiS5R&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1819)
2.  precyzyjne i zgodne z konwencją nazywanie testów
3.  7 popularnych konwencji nazewniczych - [wpis](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZkem9uZS5jb20lMkZhcnRpY2xlcyUyRjctcG9wdWxhci11bml0LXRlc3QtbmFtaW5n&sig=FSgk9Wy7bpA1AKdu8qGqFqKxVD62sHQJ2WVqv9AChLgE&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1820) (ja stosuję opcję 5, ale spotkałem się również z opcją nr 7)

7.  Stosowania sekcji

1.  G.W.T (Given, When, Then)
2.  A.A.A (Arrange, Act, Assert)
3.  ja preferuje GWT ;)

9.  Innych dobrych praktyk, a poznasz je w polecanych materiałach.

3.  Frameworka JUnit5

1.  adnotacje @Test, @Before, @DisplayName i inne
2.  Testy parametryzowane

5.  Biblioteki Mockito

1.  Czym jest Mock?
2.  Czym jest Stub?
3.  Czym jest Spy?

7.  Biblioteki AssertJ
8.  Innych bibliotek podanych w materiałach

  
Skąd się tego wszystkiego uczyć?  
  
O testach jednostkowych powstało już mnóstwo dobrych materiałów  teoretycznych i praktycznych.  
  
Będziesz mieć co robić ;)  
  
Polecane materiały (najlepiej w podanej kolejności)  

1.  Genialne wprowadzenie w unit testy - [artykuł](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZkZXZzdHlsZS5wbCUyRjIwMjAlMkYwNiUyRjI1JTJGbWVnYS1waWd1bGEtd2llZHp5LW8tdGVzdGFjaC1qZWRub3N0a293eWNoJTJG&sig=THWF5wm6v3A8UAMnasx86pzGPbMdG2wi8ozeaquQHd5&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1821)
2.  8 rzeczy, które musisz wiedzieć o testach jednostkowych na start. - [video](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZ3d3cueW91dHViZS5jb20lMkZ3YXRjaCUzRnYlM0RIN18yRWdHdzF0NA==&sig=9TxXdhDkCUNnHvZrLPBSxDCEsJs5kEGst1V6EyiihBpB&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1822)
3.  Złe testy i dobre testy na podstawie Junit5 i Mockito - [pdf](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cCUzQSUyRiUyRmthY3phbm93c2N5LnBsJTJGYm9va3MlMkZ6bGVfdGVzdHlfZG9icmVfdGVzdHkuaHRtbA==&sig=92dTzsSw95wxbs9nk21kxZKkKfz7zifR9hJvtyMTRUwy&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1823)
4.  W aplikacji Enki wybierz Java > Testing
5.  Odcinek - podcastu
6.  Jak efektywnie pisać testy jednostkowe - [video ENG](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZ3d3cueW91dHViZS5jb20lMkZ3YXRjaCUzRnYlM0RmcjFFOWFWbkJ4dyUyNnQlM0Qxcw==&sig=AezUiEc3KZKkCfkHkEmwfgAc1YRytXt4tLJq1UX4LCdy&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1824)
7.  8 znaków, że masz źle napisane testy jednostkowe - [arytkuł](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZob3d0b2RvaW5qYXZhLmNvbSUyRmJlc3QtcHJhY3RpY2VzJTJGOC1zaWducy1vZi1iYWQtdW5pdC10ZXN0LWNhc2VzJTJGJTNGdW5hcHByb3ZlZCUzRDQ1MjQ1JTI2bW9kZXJhdGlvbi1oYXNoJTNENTQ0ZWRhMDdkMTIwY2FkZDI4MTFiYWZmYTM4NmQwMzYlMjNjb21tZW50LTQ1MjQ1&sig=AvgpNvg3NctyzeqogreUuxeNpMwwFp4Yp8Gurf7ngpLx&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1825)
8.  Czym są i po co pisać testy parametryzowane - [artykuł](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZrb3ppb2xla3dlYi5wbCUyRjIwMTclMkYwNCUyRjEyJTJGanVuaXQtNS10ZXN0eS1wYXJhbWV0cnl6b3dhbmUlMkY=&sig=EtV2nSCHyXvzowkKehJbK2hDBLCfPcEeQtuAXRfEeXxP&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1826)
9.  **Kompleksowy i dłuższy kurs testów jednostkowych - [kurs](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZ3d3cudWRlbXkuY29tJTJGY291cnNlJTJGdGVzdHktamVkbm9zdGtvd2UlMkY=&sig=PkH56xmvLzFjudme27ycJFdWdU66BQAaREktAtcsXxe&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1873) ok. 40 zł**
10.  Oparty na przykładach i krótki kurs testów jednostkowych - [kurs](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZrdXJzeS5udWxscG9pbnRlcmV4Y2VwdGlvbi5wbCUyRnRlc3R5LWplZG5vc3Rrb3dlJTJG&sig=F7rLgiAorcy5nEinXQrUNpwSt4N89zAKc5A3RAp1inHr&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A2180) ok. 100 zł

  
Czas na TDD!  
  
Czym w ogóle jest TDD?  
  
Nie bez przyczyny zacząłem od testów jednostkowych.  
  
Testy można pisać nie stosując TDD.  
  
Uważam, że jeśli dopiero zaczynasz z testami, uczysz się składni, idei i dobrych praktyk, to TDD może chwilę poczekać.  
  
TDD to metoda pisania testów oparta na tym, że najpierw piszesz kod testowy, a potem dopiero produkcyjną implementację aplikacji.  
  
A po ludzku?  
  
Testujesz coś, czego jeszcze nie ma w aplikacji.  
  
Jako pierwszy krok piszesz w teście scenariusz i dopiero potem dopisujesz kod aplikacji, tak by spełnił ten scenariusz.  
  
Czyli cały czas uruchamiając taki scenariusz test będzie świecił się na czerwono (RED). Do czasu aż napiszesz taki kod, aby ten test przechodził na zielono (GREEN).  
  
Testami (test)...  
sterujesz (driveujesz)...  
rozwój (development)...  
  
Twojej aplikacji.  
  
Stąd:  

-   (test) T
-   (driven) D
-   (development) D.

  
TDD można stosować do testów jednostkowych, integracyjnych i end to end (e2e).  
  
TDD ma utarty proces działania, podzielony na 3 fazy:  

1.  faza RED
2.  faza GREEN
3.  faza REFACTOR
4.  wróć do pkt. 1. (faza RED)

  
W praktyce wygląda to tak (w dużym uproszczeniu):  

-   RED:

-   Zastanawiasz się, jaki chcesz zaimplementować przypadek testowy (piszesz scenariusz). Na przykład scenariusz:

-   Kiedy użytkownik VIP złoży zamówienie na komiks to zamówienie zostanie przyjęte, zostanie nałożona zniżka vipowska i zostaną naliczone punkty lojalnościowe.

-   Tworzysz szkielet testu w kodzie testowym.
-   Nie masz jeszcze żadnej implementacji. Robisz tylko szkielet tego co ma się zadziać. Ten szkielet robisz w testach.

-   GREEN:

-   Piszesz implementację, która powoduje, że testy z Czerwonego zamienia się w Zielony. Nie martwisz się o czystość kodu. Chcesz, tylko żeby test przeszedł.

-   REFACTOR:

-   Poprawiasz kod dbając o to, żeby test nie zmienił się z zielonego w czerwony.

-   RED:

-   Wracasz do testu i piszesz kolejny przypadek testowy.
-   Potem znowu GREEN -> REFACTOR -> RED itd. itd.

  

ŁATWE CZY TRUDNE?  

-   Jest to trudne. Dlatego niektórzy seniorzy nawet nie próbują się tego nauczyć… Co uważam za strzał w kolano, ale ok.
-   Większość juniorów, jakich znam, nie potrafi pisać w TDD, więc poprzeczka jest niska. To twoja szansa!
-   Lepiej pisać i nabierać wprawę, bo tylko praktyka pozwoli Ci opanować TDD na wystarczającym poziomie.

  
JAK SIĘ NAUCZYĆ TDD?  
Polecane materiały (najlepiej w podanej kolejności):  

1.  Ta książka to nie tylko teoria. Jest w niej super ćwiczenie. Jest to doskonały wstęp do TDD. Po prostu nie znam lepszej na początek - [książka](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZoZWxpb24ucGwlMkZrc2lhemtpJTJGdGRkLXN6dHVrYS10d29yemVuaWEtZG9icmVnby1rb2R1LWtlbnQtYmVjayUyQ3RkZHN6di5odG0lMjNmb3JtYXQlMkZk&sig=2zxeZNsULctR39scbUnGVZuMYBLKHrWLf6GcYq3FVRn7&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1827)
2.  Kompleksowa skarbnica wiedzy TDD za darmo + zadania - [strona](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZnaXRodWIuY29tJTJGdGVzdGRvdWJsZSUyRmNvbnRyaWJ1dGluZy10ZXN0cyUyRndpa2k=&sig=5bkhThYRdhDxDsvZnHst6moVpDFB9kcUZv3R45cooDRa&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1828)
3.  Trochę dla bardziej zaawansowanych  - [video ENG](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZ3d3cueW91dHViZS5jb20lMkZ3YXRjaCUzRnYlM0QydkVvTDNJcmdpdyUyNnQlM0Qxcw==&sig=AJ1xmhnKpTET3J8Dhk3vE3LwDH6vRgHsKfbfwroKUBTq&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A1829)
4.  Zbierz feedback (poniżej)

  
Warto też wspomnieć o pisaniu scenariuszy testowych na podstawie zachowań użytkowników czyli BDD (Behavior Driven Development). Połączenie BDD i TDD to majstersztyk pozwalający tworzyć testy czytelne i oparte o zachowania aplikacji a nie jej stan.  
  
Ale spokojnie, najpierw testy jednostkowe, potem TDD i BDD.  
  
Polecane materiały BDD  
1. Książka ,,BDD in Action" - John Ferguson Smart  
2. BDD kontra testy jednostkowe - [video](https://bartlomiejkalqa.lt.acemlna.com/Prod/link-tracker?redirectUrl=aHR0cHMlM0ElMkYlMkZ3d3cueW91dHViZS5jb20lMkZ3YXRjaCUzRnYlM0RZTDFxM3REZ0ltTQ==&sig=HCCSucAtecFnUzCWvAFcyconE6rExpFidpVfWg5YQAcy&iat=1651928790&a=%7C%7C90494724%7C%7C&account=bartlomiejkalqa%2Eactivehosted%2Ecom&email=%2Fik9Q6GNC71hPJcwY%2BjbE6ayix7bu3JGazpjEK6xMr8%3D&s=05b3708f560fde7a9c7ef28284edb9e2&i=346A395A1A2189) ENG


=====================================================

## **1. Przerób książkę:** **_Java. Techniki zaawansowane. Wydanie XI - C. Horstmann_**

**Dlaczego ta książka?**

Bo jest to kontynuacja pierwszej książki, którą polecałem. Jeśli polubiłeś **Horstmanna** jako autora, to jego kolejna książka będzie dla Ciebie idealna.

Czy masz przeczytać całą książkę od **deski do deski**? Nie polecam.

Podam Ci, jakie rozdziały najlepiej przeczytać, żeby **nie tracić czasu** na naukę niepotrzebnych rzeczy.

**Rozdział 1: Biblioteka Stream (30 stron)**

**Dlaczego warto poznać ten temat?**

Java **strumieniami** stoi. Na każdej rozmowie rekrutacyjnej będą Cię o to pytać. Jest to po prostu wykorzystywane w projektach komercyjnych. Zapoznaj się **metodami**, które wystawia nam tzw. Stream API Javy. Te metody wypisałem poniżej.

Najczęściej korzystam z pogrubionych:**_map_**_,_ _**flatMap**__,_ _**filter**__, sorted, limit, count, findAny,_ _**findFirst**__, allMatch, anyMatch, reduce, forEachOrdered, peek,_ _**collect**_​  
​  
Polecam Ci nic innego jak starą dobrą praktykę. Potestuj sobie każdą z tych funkcji na kolekcjach (najlepiej z wieloma elementami).

**Rozdział 2: Wejście** (IN) **i Wyjście** (OUT) **(80 stron)**

**Dlaczego warto poznać ten temat?**

Praca na plikach to dzień powszedni w **małych projektach**. Ale to tylko początek. Pliki przyjmuje się do aplikacji (IN) i dane zapisuje się nie tylko w plikach, ale np. w bazie danych (OUT). Zacznij od czegoś prostego (od książki), a dopiero potem przejdziemy do trudniejszych zagadnień związanych z odczytem i zapisem danych z baz danych.

**​  
Rozdział 6: API dat i czasu (20 stron)**

**Dlaczego warto poznać ten temat?**

Większość aplikacji jest oparta o czas. Dlatego warto poznać **dobre praktyki** i **polecane typy** w Javie do obsługi czasu i dat.

​  
​**Rozdział 3: Język XML**

**Dlaczego warto poznać ten temat?**

Głównie ze względu na:

Po pierwsze Mavena,

Po drugie starsze projekty, które wykorzystują ten format w komunikacji sieciowej oraz do różnych konfiguracji bibliotek.  
​  
Warto znać ten format, ale możesz trafić do firmy, która w ogóle **nie korzysta z XML’a.** A korzystają na przykład z JSON’a albo YAML’a.  
​

**Rozdział 7: Internacjonalizacja (40 stron)**

**Dlaczego warto poznać ten temat?**

Raz stworzona aplikacja może działać w wielu krajach (skalować się). Dlatego czasami w aplikacjach stosuje się **wielojęzyczność** - przeczytaj ten rozdział, bo prawdopodobnie może Ci się przydać w przyszłości, gdy będziesz pisać aplikację w kilku językach (oczywiście mowa tutaj o języku użytkowników aplikacji).  
​

**Rozdział 9: Bezpieczeństwo**

**Dlaczego warto poznać ten temat?** Temat rzeka. W tej książce jest tylko **zalążek tematu** bezpieczeństwa w aplikacjach. Z praktyki wiem, że programiści i tak zazwyczaj dopiero na poziomie mida/seniora zaczynają wchodzić w głębsze meandry **Security**. Dlatego potraktuj ten rozdział **opcjonalnie** na tym etapie. Warto też posłuchać tego [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/dpheh0hq6qg908tm/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj05TFJaWGcwTks1aw==) o oAuth2  
​

**Polecane Materiały** (jeśli nie chcesz czytać książki)

1.  Przegląd interfejsów funkcyjnych w Javie 1 - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/e0hph7hkvkg304a8/aHR0cHM6Ly93d3cuamF2YXBwYS5jb20va3Vycy1qYXZhL2phdmE4L3ByemVnbGFkLWludGVyZmVqc293LWZ1bmtjeWpueWNo)​
2.  Przegląd interfejsów funkcyjnych w Javie 2 - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/7qh7h8h0l072o3sz/aHR0cHM6Ly9jb2RlY291cGxlLnBsLzIwMTYvMTAvMDgvaW50ZXJmZWpzeS1mdW5rY3lqbmUv)​
3.  Java - Interfejsy funkcyjne - [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/owhkhqh494vmrxhv/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1DamV4SDRBLTltOA==)​
4.  Java Stream API - [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/z2hghnho6ov23nbp/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1xNHMwYUUzRm5DQQ==)​
5.  Dla bardziej zaawansowanych: jeśli chcesz poczytać o programowaniu funkcyjnym/reaktywnym:
    1.  Functional reactive programming w Javie - [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/p8heh9h9690wz6hq/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1TN2dDY2dUV1NQcyZ0PTM4MDRz)​
    2.  RxJava in legacy projects - [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/x0hph6hn2n6vw0f5/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1hWEJxMUxRU3Jrcw==)​

---

## **2. Pamięć, wątek, proces i stos w Javie**

**Jakie pytania sobie zadawać przy nauce tych tematów?**​  
Wszystkie rzeczy, które powinieneś wiedzieć wypisałem pod danym tematem.  
Każdy z tych tematów jest pokryty w Polecanych Materiałach oraz w książce, o której zaraz więcej opowiem (jest MEGA dobra)  
​  
​**Ale co dokładnie trzeba wiedzieć?**​  
​  
​**a) Bardziej w kontekście codziennej pracy programisty:**​  
​**Wątek i proces oraz proces vs wątek.**

1.  Czym jest tak naprawdę wątek w Javie?
2.  Ile wątków jest w klasycznej webowej aplikacji po jej uruchomieniu?
3.  Ile wątków Twoja aplikacja jest w stanie mieć?
4.  Jak zarządzać wątkami?
5.  Jakie typowe problemy mogą występować podczas synchronizacji wątków
6.  Poznaj różnice między wątkiem a procesem

**Pamięć RAM**

Musisz być świadomy tego, że Twoja aplikacja ma ograniczenia związane z pamięcią podręczną.

**Stos**

Po co jest stos? Co jest umieszczane na stosie? Jakie problemy mogą być związane z przepełnieniem stosu? Jak zarządzać stosem?

​  
​**Pule wątków**

Czym są? Dlaczego warto je używać, zamiast korzystać z tworzenia pojedynczych wątków za pomocą klasy Thread w Javie?  
​  
​**ExecutorService w Javie**

Klasa w Javie, która pomogą zarządzać wątkami.

**Czy da się takie rzeczy obserwować w swojej aplikacji?**

Jak na bieżąco kontrolować stan swojej aplikacji? Jak sprawdzić ile ma aktualnie wątków i co to są w ogóle za wątki? Ile aplikacja aktualnie wykorzystuje pamięci RAM, ile ma procesów i co jest na ich stosach? Jak sprawdzić statystyki wirtualnej maszyny Javy (JVM)? Ile jest obiektów na stercie i ile trwają procesy czyszczenia Garbage Collectora? Najprościej skorzystać z programu VisualVM. Ale tak naprawdę w większych aplikacjach najczęściej konfiguruje się ją pod to by wystawiała **statystyki** tzw. metryki, które potem można pobrać za pomocą np. **Prometheusa**. Jeśli aktualnie ten temat jest dla Ciebie zbyt skomplikowany to po prostu idź dalej. Wrócisz do tego w przyszłości :)  
​  
​**b) Bardziej w kontekście rozmów rekrutacyjnych**

**Jak działa Garbage Collector w Javie?**

Sztandarowe pytanie na rekrutacjach. Ja nauczyłem się tego jak działa GC z tych dwóch artykułów ([część 1](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/6qheh8hprpg87gbo/aHR0cHM6Ly9kb2NzLmdvb2dsZS5jb20vdmlld2VyP3VybD1odHRwcyUzQSUyRiUyRmJvdHRlZ2EuY29tLnBsJTJGcGRmJTJGbWF0ZXJpYWx5JTJGanZtJTJGanZtMS5wZGY=) i [część 2](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/kkhmh6h8w8q0l0sl/aHR0cHM6Ly9kb2NzLmdvb2dsZS5jb20vdmlld2VyP3VybD1odHRwcyUzQSUyRiUyRmJvdHRlZ2EuY29tLnBsJTJGcGRmJTJGbWF0ZXJpYWx5JTJGanZtJTJGanZtMi5wZGY=)). Polecam Ci gorąco wydrukować sobie je, pisać po nich, rysować na kartce. Zrozumiesz, że w gruncie rzeczy jest to łatwe, jeśli rozłożysz to na mniejsze części :) Pamiętaj, że to jest temat typu must-have. Po prostu musisz to ogarniać.

Dlaczego? Java jest oparta o JVM, a w JVM mamy Garbage Collector więc jeśli korzystasz z Javy, to musisz poznać to jak ona w ogóle działa.

**Czym jest Heap w Javie? (sterta)**

Odpowiedź znajdziesz w poniższych materiałach dotyczących modelu pamięci w Javie.

**Jak Java zarządza pamięcią?**​  
​[Ten](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/58hvh7h5x58dmri6/aHR0cDovL3R1dG9yaWFscy5qZW5rb3YuY29tL2phdmEtY29uY3VycmVuY3kvamF2YS1tZW1vcnktbW9kZWwuaHRtbA==) artykuł to **wszystko, co musisz wiedzieć** na temat modelu pamięci Javy. Dowiesz się czym jest Stos Wątku, czym w ogóle jest Stos, czym jest Heap w Javie. Jak obiekty są przechowywane w Javie. Jaki to wszystko ma związek z RAM'em i CPU komputera. Dowiesz się o typowym problemie, który możesz napotkać na swojej drodze, czyli Race Condition. Dla wzrokowców - wersja [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/25h2hoh797zp2mu3/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1MQ1NxWnlqQndXQSZsaXN0PVBMTDh3b01Id3IzNkVEeGpVb0N6Ym9aamVkc25oTFAxajQmaW5kZXg9Mw==)**​**

**Polecane Materiały**

1.  Podstawy Modelu Pamięci w Javie - [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/qvh8h7h8w85mrlhl/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1MQ1NxWnlqQndXQQ==)​
2.  Podstawy Wątków w Javie na przykładach kodu - [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/g3hnh5he9e5832tr/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1lUWs1QVdjVFM4dyZsaXN0PVBMTDh3b01Id3IzNkVEeGpVb0N6Ym9aamVkc25oTFAxajQmaW5kZXg9Mw==)​
3.  Powrót do podstaw: wątki - [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/9qhzhnhgwgmvp7c9/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1SVkJsQ1RLXzNvQSZ0PTQ3NnM=) PL - dubiel o watkach
4.  Co to jest JVM? Jak działa Java? - [pdf](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/3ohphkhqmql536hr/aHR0cHM6Ly9ib3R0ZWdhLmNvbS5wbC9wZGYvbWF0ZXJpYWx5L2p2bS9qdm0xLnBkZg==)​
5.  GarbageCollector i Heap w Javie - [pdf](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/n2hohvhnqnp9v8f6/aHR0cHM6Ly9ib3R0ZWdhLmNvbS5wbC9wZGYvbWF0ZXJpYWx5L2p2bS9qdm0yLnBkZg==)​
6.  15 narzędzi do monitorowania Twojej aplikacji - [lista](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/48hvheh0l0edmpix/aHR0cHM6Ly9zZW1hdGV4dC5jb20vZ3VpZGVzL2phdmEtbW9uaXRvcmluZy8=)​

---

**3. Wielowątkowość**

**Jak to się ma w praktyce?**

Programowanie w wielu wątkach to znana cecha programów pisanych w Javie. Szybkie przetwarzanie danych i bezpieczne wykorzystywanie potencjału maszyny, na którym jest włączona aplikacja to coś, co warto mieć na uwadze.

Istnieje wiele dobrych praktyk dotyczących projektowania aplikacji działających na wielu wątkach. Naucz się ich i nie popełniaj typowych błędów.

**Niemutowalność**

Kluczowa dobra praktyka przy projektowaniu aplikacji wielowątkowych! Więcej o tym w książce Java Efektywne Programowanie.

**Asynchroniczność, równoległość, współbieżność i wielowątkowość**

Co odróżnia te terminy od siebie?

**Czy znasz pakiet java.util.concurrency?  
​**Pakiet zawiera gotowe komponenty do tworzenia wydajnych wielowątkowych aplikacji odpornych na typowe błędy. Znajdziesz to w polecanej książce Java Concurrency In Practice

**Co wiesz o wielowątkowości?  
​**Wielowątkowość w Javie to złożony temat. Najlepiej wejść w niego z tym [**filmikiem**](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/wnh2hghr7rp2q4f7/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1tVEdkdEM5ZjRFVSZ0PTQwMnM=). Następnie polecam Ci książkę **Java Concurrency in Practice** - nie ma lepszej książki do poznania wielowątkowości w Javie. Znajdziesz w niej wszystko, co powinieneś wiedzieć np. używanie zmiennych typu **Atomic** i ogólnie pakietu **java.util.concurrent**. Po zapoznaniu się z tymi materiałami osoby Cię rekrutujące będą musiały Ci przerywać, bo tyle będziesz wiedzieć o wielowątkowości :)**​  
​  
Polecane Materiały**

1.  Java Współbieżność i Wielowątkowość Wprowadzenie - [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/reh8hohqdqrlmvt2/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1tVEdkdEM5ZjRFVSZsaXN0PVBMTDh3b01Id3IzNkVEeGpVb0N6Ym9aamVkc25oTFAxajQmaW5kZXg9Mg==) ENG (14 minut)
2.  Stosowanie ExecutorService część 1 - [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/08hwh9hmem562kcl/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1OYjg1eUoxZlBYTSZsaXN0PVBMTDh3b01Id3IzNkVEeGpVb0N6Ym9aamVkc25oTFAxajQmaW5kZXg9MTQ=) ENG
3.  Stosowanie ExecutorService część 2 - [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/8ghqhohgdgv6o5fk/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1NQl9xQ1hCU2dLMCZsaXN0PVBMTDh3b01Id3IzNkVEeGpVb0N6Ym9aamVkc25oTFAxajQmaW5kZXg9MTU=) ENG
4.  Asynchroniczność, czyli CompletableFuture in Java 8 - [video ENG](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/vqh3hrhn0n79onhg/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj0tTUJQUTdOSUxfWSZ0PTE0MDFz)​
5.  Książka _Java Concurrency in Practice_: Goetz Brian, Peierls Tim - mega!

---

## **​  
4. Przeczytaj tematy z książki** **_Java Efektywne Programowanie_**

**3 powody, dla których warto przerobić tę książkę**

1.  Autorem jest jeden z twórców Javy: Joshua Bloch - inżynier oprogramowania, obecnie pracujący w Google. Prowadził projekt i implementację licznych funkcjonalności języka i platformy Java, między innymi Java Collections.
2.  Programiści korzystają z tych praktyk w codziennej pracy w Javie, są to rzeczy, z których wszyscy korzystają i wiedzą, że tak trzeba robić, ale niekoniecznie każdy wie, że jest to z tej książki ;)
3.  Wiele rzeczy, o których dzisiaj wspomniałem jest pokrytych w tej książce. **SIC!**

Nie jestem fanem przerabiania całych książek na sucho, dlatego wskażę Ci tylko wymagane minimum, które warto poznać.**​  
​  
​**Przejdźmy do…

## **18 tematów, które musisz poznać:**

**Temat 3: Wymuszanie właściwości Singleton za pomocą prywatnego konstruktora lub typu enum  
​**Dlaczego warto poznać ten temat?**​  
​**Warto wiedzieć czym jest Singleton, ponieważ w pracy spotkasz się z tym bardzo często - a na pewno na Twojej rozmowie rekrutacyjnej padnie pytanie o ten wzorzec

**Temat 5: Wstrzykiwanie zależności  
​**Dlaczego warto poznać ten temat?**​  
​**Jak widzisz nie tylko w Springu jest Wstrzykiwanie Zależności. Możesz to uzyskać w Javie. Poznaj ten mechanizm, a potem będzie Ci łatwiej zrozumieć Springa. Zalet wstrzykiwania jest mnóstwo. Na przykład łatwiejsze testowanie aplikacji czy zmniejszanie zależności między klasami.

**Temat 9: Try z zasobami (try with resources)  
​**Dlaczego warto poznać ten temat?**​  
​**Try i catch to składnia, którą będziesz często spotykać i używać. Warto się nauczyć jej ulepszenia, czyli try with resources.

**Temat 10: Zachowywanie założeń w trakcie redefiniowania metody equals  
​**Dlaczego warto poznać ten temat?**​  
​**Kolejny sztandar Javy, czyli metoda equals. Po prostu przeczytaj :)

**Temat 15: Ograniczanie dostępności klas i ich składników  
​**Dlaczego warto poznać ten temat?**​  
​**Będziesz projektować aplikacje obiektowe tak jak powinno się to robić. Jeśli masz problem z obiektowością to ta zasada pomoże Ci zrozumieć, dlaczego warto pisać w ten sposób kod i jak robić to dobrze.

**Temat 17: Zapewnienie niezmienności obiektu**

Dlaczego warto poznać ten temat?

Immutability (niezmienność) to coś, co pomaga utrzymać aplikację w stanie w takim, jakim się możesz tego spodziewać.

Jest to GameChanger jeśli chodzi o aplikację wielowątkowe. Podejście **nie modyfikuj obiektu**, **a stwórz nowy ze zmienionymi danymi** powoduję, że Twoja aplikacja staje się bardziej przewidywalna i obiekty tworzone w aplikacji mają swoją historię, do której możesz łatwo wrócić w razie problemów. **SUPER WAŻNE zagadnienie, a na rozmowach rekrutacyjnych będą o to pytać.**

**Temat 18: Zastępowanie dziedziczenia kompozycją  
​**Dlaczego warto poznać ten temat?**​  
​**Jest to dobra praktyka, która pozwala uniknąć wielu problemów z designem Twojej aplikacji. Warto stosować dziedziczenie tylko i wyłącznie z rozwagą i odpowiednim przemyśleniem. Wszystko jest w książce :)

**Temat 26: Nie korzystaj z typów surowych  
​**Dlaczego warto poznać ten temat?**​  
​**Chodzi o zarządzanie pamięcią w Javie. Typy surowe są może i mniej pamięciożerne, ale to z obiektów słynie Java. Obiekty są przechowywane na Stercie i są czyszczone przez GarbageCollector.

**Temat 34: Użycie typów wyliczeniowych zamiast stałych int  
​**Dlaczego warto poznać ten temat?**​  
​**Enum jest świetnym narzędziem do ograniczania możliwości wybrania jakiejś konkretnej opcji w aplikacji. Dodatkowo prosty zestaw nazw to coś, co lubią programiści.

**Temat 42: Stosuj lambdy zamiast klas anonimowych  
​**Dlaczego warto poznać ten temat?**​  
​**Po prostu lambdy są powszechnie używane w codziennej pracy w Javie i zastąpiły podejście tworzenia klas anonimowych.

**Temat 44: Korzystaj ze standardowych interfejsów funkcyjnych  
​**Dlaczego warto poznać ten temat?**​  
​**Istnieje zestaw gotowców, które warto znać i mieć w swoim asortymencie, tymi gotowcami są typowe interfejsy funkcyjne (z resztą było dzisiaj trochę o nich :))

**Temat 45: Rozważnie korzystaj ze strumieni  
​**Dlaczego warto poznać ten temat?**​  
​**Strumienie nie są dobrem objawionym. Mają swoje ograniczenia i przypadki użycia.

**Temat 54: Zwracanie pustych tablic lub kolekcji zamiast null  
​**Dlaczego warto poznać ten temat?**​  
​**Dobrze zaprojektowana aplikacja nie powinna doprowadzać do sytuacji, w których aplikacja wybucha.

**Temat 60: Unikanie typów float, double gdy potrzebne są dokładne wyniki  
​**Dlaczego warto poznać ten temat?**​  
​**Na przestrzeni lat zostało popełnionych mnóstwo błędów jeśli chodzi o dokładność wyników po przecinku. Poznaj najlepsze praktyki.

**Temat 62: Unikanie typu String gdy są bardziej odpowiednie typy**

Dlaczego warto poznać ten temat?

Typowym nawykiem początkujących i osób, które nie zastanawiają się nad designem aplikacji jest wykorzystywanie wszędzie typu String. Po to można tworzyć własne klasy, aby zapobiec problemom. Wyobraź sobie, że metoda przyjmuje trzy argumenty typu String. Jeśli pomylisz się w kolejności przekazywania do niej argumentów, to aplikacja nadal będzie się kompilować i o błędach możesz dowiedzieć się dopiero na produkcji. Bo ktoś zamiast firstName podał lastName.

**Temat 68: Wykorzystanie ogólnie przyjętych konwencji nazewnictwa  
​**Dlaczego warto poznać ten temat?**​  
​**Warto poznać praktyki osób pracujących np. w Google czy Amazonie. Wtedy będziesz tworzyć kod zrozumiały nie tylko przez Ciebie, ale innych programistów - co świadczy o Twojej dojrzałości jako ekspert/ka.

**Temat 69: Wykorzystanie wyjątków w sytuacjach nadzwyczajnych  
​**Dlaczego warto poznać ten temat?**​  
​**Nauczysz się stosować wyjątki w odpowiednich do tego sytuacjach. Łatwo nadużywać tego mechanizmu, co może być kosztowne ze względu na wydajność aplikacji.

**Temat 80: Stosowanie Executorów, Tasków i Streamów zamiast Wątków  
​**Dlaczego warto poznać ten temat?**​  
​**Warto poznać dobre praktyki wielowątkowości. Pokrywa się to z tematami z książki Java Concurrency in Practice.

**Polecane Materiały**

W tym przypadku nie polecę innych źródeł niż powyższa książka (Java Efektywne Programowanie), ponieważ większość z nich bazuję na tej właśnie książce! Warto czerpać wiedzę ze źródełka co Tobie polecam zrobić :)

---

## **5. Java i różne różności**

**Wyjątki w Javie**

Najważniejsze w tym temacie to:

1.  Jaka jest różnica między wyjątkami typu Checked a Unchecked?
2.  Jak wygląda hierarchia wyjątków w Javie?
3.  Co znaczą wyjątki **RuntimeException**, **IllegalStateException**, **NullPointerException**, **StackOverflowException**

**Polecane Materiały (Wyjątki w Javie)**

1. Wyjątki w Javie - podstawy - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/l2hehmho2o9ml3b6/aHR0cHM6Ly9rb2JpZXR5ZG9rb2R1LnBsL25pZXpiZWRuaWstanVuaW9yYS13eWphdGtpLWktaWNoLW9ic2x1Z2Ev)​

2. Wyjątki kontrolowane vs niekontrolowane w Javie. O co chodzi? - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/m2h7h5ho5op633hm/aHR0cHM6Ly8xMDI0a2IucGwvcmVrcnV0YWNqYS9jaGVja2VkLXZzLXVuY2hlY2tlZC1leGNlcHRpb25zLw==)​

---

**Jak dokładniej działają kolekcje Javie i jakie wybierać?**

Jak to jest, że czasami używa się **List**, a czasami **Array**, albo **Set**, **Queue** czy **Map**? Spójrz na schemat kolekcji w Javie (możesz go wydrukować i powiesić w dobrze widocznym miejscu: lodówka/ściana). [źródło i wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/dpheh0hq6qg9e8im/aHR0cHM6Ly93d3cuamF2YXRwb2ludC5jb20vY29sbGVjdGlvbnMtaW4tamF2YQ==).

![[collection.webp]]
Description automatically generated](https://embed.filekitcdn.com/e/PnRL2gAKLh5sBLF3edZhT/71AKXfjyy2ciuq32aN6D1Q)

Następnie warto poznać jakie **zastosowania** mają konkretne kolekcje. Jest to związane mocno ze złożonością obliczeniową operacji: **dodawania**, **usuwania**, **szukania** oraz **dostępu do konkretnego elementu** w danej kolekcji. Aby porównywać efektywność i dobierać odpowiednią kolekcję do Twoich problemów polecam korzystać z [tej](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/e0hph7hkvkg374t8/aHR0cHM6Ly93d3cuYmlnb2NoZWF0c2hlZXQuY29tLw==) ściągi.  
​  
Na spokojnie poznawaj sobie poszczególne kolekcje. Listy, Sety, a potem Mapy, Kolejki itd. Najlepiej jeśli przerobisz [te](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/7qh7h8h0l07293sz/aHR0cHM6Ly93d3cuamF2YXBwYS5jb20va3Vycy1qYXZhL2tvbGVrY2plLXdwcm93YWR6ZW5pZQ==) 4 lekcje.  
​  
​**Polecane Materiały (kolekcje w Javie)**

1.  Czym jest złożoność obliczeniowa i notacja O? - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/owhkhqh494vmwxcv/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1uWGFVSXd3Y1QySQ==)​
2.  Co jest szybsze? O(1) czy O(lg n)? Dlaczego? - [wątek](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/z2hghnho6ov2encp/aHR0cHM6Ly93d3cucXVvcmEuY29tL1doaWNoLWlzLWZhc3Rlci1PLTEtb3ItTy1sZy1uLVdoeQ==)​
3.  100 pytań rekrutacyjnych na temat struktur danych i algorytmów w Javie - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/p8heh9h9690w46sq/aHR0cHM6Ly93d3cuamF2YTY3LmNvbS8yMDE4LzA2L2RhdGEtc3RydWN0dXJlLWFuZC1hbGdvcml0aG0taW50ZXJ2aWV3LXF1ZXN0aW9ucy1wcm9ncmFtbWVycy5odG1sP209MQ==)​
4.  Jak operować na ogromnym pliku danych (10GB)? - [wątek na forum](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/x0hph6hn2n6ve0h5/aHR0cHM6Ly93d3cuY2FyZWVyY3VwLmNvbS9xdWVzdGlvbj9pZD01MDgyMzE2MzY5MDM1MjY0)​

---

**Idempotentność**​  
Ważne zagadnienie podczas tworzenia oprogramowania. Najłatwiej wytłumaczyć je w ten sposób.

​

![A picture containing text, indoor, blue, machine
Description automatically generated](https://embed.filekitcdn.com/e/PnRL2gAKLh5sBLF3edZhT/g6YzX9ubG2usjbXRLSPGt)

​  
​**PRZYKŁAD 1:**

Przyciski włączania/wyłączania kierunkowskazu w tramwaju. Naciśnięcie przycisku WŁĄCZ (zielony) jest operacją idempotentną, ponieważ ma ten sam efekt, niezależnie od tego, czy jest wykonywana raz, czy wiele razy. Podobnie naciśnięcie WYŁĄCZ jest idempotentne.  
​  
​**PRZYKŁAD 2:**

A w programowaniu? Tak samo jest jeśli chodzi o metodę PUT z RESTA. Powinna zachować idempotentność. Wiele razy wysłane zapytanie o aktualizację zasobu (takim zasobem może być np. rezerwacja w hotelu) nie powinno powodować, żadnych niepożądanych efektów ubocznych. Za pierwszym razem zmodyfikuję dane, a potem wszystkie kolejne takie same requesty powinny nadpisywać te dane. Czyli taki case: Użytkownik chce zmienić godzinę przyjazdu w swojej rezerwacji hotelowej z 12:00 na 13:00? Wysłanie stu requestów PUT z jego aplikacji ze zmienioną godziną przyjazdu na 13:00 nie powinno być problemem i za każdym razem endpoint powinien zwracać tę samą odpowiedź. W przeciwieństwie do PUT mamy POST, która jest nieidempotentny. Wywołując wielokrotnie POST możesz spodziewać się stworzenia wielu nowych zasobów. (100 takich samych requestów = 100 nowych rezerwacji). Oczywiście w idealnym świecie (usługa może przecież dać odpowiedź, że nie ma już wolnych miejsc).  
​  
​**Polecane Materiały (Idempotentność)**

1. Idempotentność w REST - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/6qheh8hprpg8lgco/aHR0cHM6Ly9yZXN0ZnVsYXBpLm5ldC9pZGVtcG90ZW50LXJlc3QtYXBpcy8=) ENG

---

## **4 formaty danych, które warto poznać**

1. Pliki .json - komunikacja w sieci, konfiguracja w bibliotekach

2. Pliki .xml - w Mavenie i czasami w pracy w komunikacji

3. Pliki .yml i .yaml - docker, konfiguracja w bibliotekach

4. Pliki .properties - ustawienia

​  
​**Polecane Materiały (4 formaty danych)**​  
1. JSON w 10 minut - [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/kkhmh6h8w8q0n0fl/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1paUFEaENoUnJpTQ==) ENG

---

## **Servlety**

Każde zapytanie HTTP do twojej aplikacji jest obsługiwane przez Servlety. Np. GET, przez doGet(). Warto zapoznać się jak to jest zaimplementowane. Wykorzystuje to Spring MVC (Spring Web).

Servlety nie występują w aplikacjach opartych o **programowanie reaktywne (Spring Webflux)**, które jest oparte o strumienie danych. W strumieniu danych albo dane są albo ich nie ma i po tym stwierdza się, że powinno się obsługiwać zapytanie.  
​

**Polecane Materiały (Servlety)**​  
1. Servlety – aplikacje sieciowe - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/58hvh7h5x58dgrb6/aHR0cHM6Ly9wcm9ncmFtaXN0YWphdmEucGwvc2VydmxldHkv)​  
2. Czym są servlety? - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/25h2hoh797zp3mf3/aHR0cHM6Ly9qYXZhc3RhcnQucGwvYmF6YS13aWVkenkvc2xvd25pay9zZXJ2bGV0)​

---

**Protokół HTTP  
​**Jest to aktualnie najbardziej popularny protokół komunikacji sieciowej.**​  
​**Co warto poznać w tym temacie?

**Nagłówki HTTP**

Jakie nagłówki są najważniejsze? Link w polecanych materiałach.

**Kody odpowiedzi HTTP  
​**W praktyce najważniejsze to 404, 200, 201, 202, 500, 503**​  
Czym jest Request HTTP i Response HTTP?  
​  
Czasowniki HTTP.  
​**Najważniejsze to GET, POST, PUT, DELETE, PATCH**​  
​  
Implementacje klientów HTTP w Javie.**

Na moich rozmowach padały pytania o klientów HTTP. Mówi się na to klienci, bo tak naprawdę są to implementacje czegoś, co korzysta (jest klientem) z protokołu HTTP.

Dzięki takiemu klientowi nie musisz pisać niskopoziomowego kodu, tylko masz do wykorzystania wygodne metody. Na przykład: W Springu jest klient RestTemplate, który ma metodę exchange, która pozwala w łatwy sposób np. pobrać jakieś dane z innej usługi GET'em. Np. dane pogodowe na najbliższe 7 dni z weather.com. Czyli w dużym uproszczeniu Ci klienci używają metod POST, GET, PUT, DELETE, aby przekazać jakieś dane do innej usługi HTTP, która ma swojego klienta, który oczekuje na takie zapytania.

Jest to ważny temat z perspektywy backend developera, więc musisz go poznać tak blisko jak się tylko da. Będziesz korzystać z tej wiedzy w pracy na sto procent. Odpowiednie dla Ciebie na start to…

Bardzo polecam Ci przyswoić sobie wiedzę z tej bardzo dobrej [**prelekcji**](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/qvh8h7h8w85mdlsl/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1kY1V3QXdjTHhIaw==) (tylko 42 minuty, a zmienia perspektywę na całe życie). Dzięki temu nie będziesz mieć żadnych problemów związanych z klientami HTTP na swoich rozmowach rekrutacyjnych, a nawet dzięki temu zabłyśniesz w oczach rekruterów!

Proszę nie olej tego tematu! Kilka osób mi potwierdziło, że ta wiedza przydała im się na ich rozmowach rekrutacyjnych. I faktycznie potrafili się wybronić z HTTP!  
​  
​**Obsługa błędów w HTTP  
​**Jak zabezpieczyć się przed problemami z komunikacją po HTTP? Czym jest Circuit Breaker? Czym są timeouty i jak je ustawiać? Oglądaj od 1:28:0 to [video](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/9qhzhnhgwgmvd7t9/aHR0cHM6Ly95b3V0dS5iZS9HYy1WamNFOW5Ybz90PTUzMzA=)**​  
​**​  
​**Polecane Materiały (HTTP)**

1. 5 najważniejszych nagłówków protokołu HTTP - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/3ohphkhqmql546ar/aHR0cHM6Ly9hbGV4eml0b3dvbGYubWVkaXVtLmNvbS90aGUtNS1tb3N0LWltcG9ydGFudC1odHRwLWhlYWRlcnMtZDllOWY5NGJiMWY2)​

---

## **REST - co warto wiedzieć?**

1. Czym jest REST?

2. REST jest bezstanowy - co to znaczy?

3. Czym jest zasób w REST?

4. Jakie czasowniki są dostępne? Do czego stosuje się jakie?

5. Co to są 4 dojrzałości RESTa?

​  
​**Polecane Materiały (REST)**

1. Poradnik od developerów Google - jak zacząć z REST? - [tutorial](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/n2hohvhnqnp968t6/aHR0cHM6Ly9kZXZlbG9wZXJzLmdvb2dsZS5jb20vZml0L3Jlc3QvdjEvZ2V0LXN0YXJ0ZWQ=)​

2. 4 dojrzałości RESTA - jak robić dobrego RESTA? - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/48hvheh0l0ed6pix/aHR0cHM6Ly9qYWt6b3N0YWNwcm9ncmFtaXN0YS5uZXQvMjAyMC8xMS8yNS9yZXN0LWFwaS1tb2RlbC1kb2pyemFsb3NjaS1yaWNoYXJkc29uYS8=)​

3. Bezstanowość w REST - [wpis](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/wnh2hghr7rp2x4h7/aHR0cDovL3NlYmFzdGlhbmN6ZWNoLmNvbS8yMDE3LzAyLzIwL2NlY2h5LWRvYnJlZ28tcmVzdGZ1bC1hcGkv)​

---

## **Lista fundamentów część 3.**

Sprawdź [listę](https://click.convertkit-mail2.com/wvu385gmdvb6ungpl5i7/reh8hohqdqrlwvi2/aHR0cHM6Ly9mb2FtLWVsZi04ZDYubm90aW9uLnNpdGUvRnVuZGFtZW50eS1KYXZ5LWt0LXJlLW11c2lzei16bmEtQ3otMi0xMzhjZjIyMzgyMDk0NzQwYmE2MTdjYjAxMGI2ODU1NA==) **fundamentów** Javy, które musisz znać **(część 3)**. Doczytaj na temat tych rzeczy, które są Ci jeszcze obce.

Chodzi o to, by **mniej więcej wiedzieć**, o co chodzi w danym temacie.

**Nie musisz wszystkiego ryć na blachę!**

I tak będziesz wracać do teorii wtedy gdy zajdzie potrzeba zastosować tę wiedzę w swoim projekcie.

To jest piękne, bo na **100%** będziesz zmuszony/a skorzystać z tych fundamentów - w przeciwnym wypadku nie będziesz w stanie pójść dalej ze swoimi projektami.

=============================================

## **1:** Moduł powinien odpowiadać za jakiś **konkretny proces**

Przykłady procesów to:

1.  Proces 1: Obliczanie kosztów zamówienia to **proces**, więc zrób moduł **costcalculator**
2.  Proces 2:. Tworzenie pdfa to **proces**, więc zrób moduł **pdfgenerator**
3.  Proces 3: Tworzenie faktury to **proces**, więc zrób moduł **invoicecreator**
4.  Proces 4: Wysyłanie maila to **proces**, więc zrób moduł **emailsender**

Często każdy z tych modułów to po prostu **pakiet w Javie**.

W takim pakiecie zwykle robimy trzy lub więcej podpakietów, ale to nie jest reguła:

1.  **application**
2.  **domain**
3.  **infrastructure**

Na poniższym obrazku mógłbym w każdym module tworzyć takie pod pakiety **application**, **infrastructure** i **domain**, ale tak naprawdę to jest kwestia umowna i wolę jak klasy domenowe i aplikacji są płasko na tym samym poziomie, bo widzę co dany moduł robi i nie muszę szukać w pod pakietach.

Infrastruktura jest wyjątkiem - ma swój pod pakiet oraz pakiet **dto,** w którym trzymam wszystkie klasy publiczne, które służą **tylko za reprezentacje danych systemu**, są one zwracane przez Controllery.

​

![Text
Description automatically generated](https://embed.filekitcdn.com/e/PnRL2gAKLh5sBLF3edZhT/j9TQXaZCqvB7UrogepXJHR)

​[Kod](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/n2hohvhnqnz64oc6/aHR0cHM6Ly9naXRodWIuY29tL2thbHFhL2RlbW8=) na githubie.

Dzięki takiemu podziałowi na moduły **zmniejsza się** coś takiego jak [cognitve load](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/dpheh0hq6ql8x6am/aHR0cHM6Ly90ZW90dGkuY29tL2NvZ25pdGl2ZS1vdmVybG9hZC1pbi1zb2Z0d2FyZS1kZXZlbG9wbWVudC8=).

Przeładowanie kognitywne, to w skrócie znaczy, że im mniejszy ładunek w głowie, tym łatwiej skupić się na implementacji **jednego konkretnego modułu** nie myśląc w tym czasie o innych modułach.

Do takich **czterech modułów** może usiąść teraz **czterech różnych programistów**.

Jednakże te moduły finalnie mają ze sobą współpracować, dlatego, **muszą oni na początku ustalić jak będzie wyglądać API** każdego modułu (będą to metody publiczne w fasadach).

Wtedy mogą zacząć pracować równolegle nad każdym z modułów.

Unikamy sytuacji, w której programista implementujący moduł **emailsender** **musiałby czekać** aż prace nad modułem **pdfgenerator**, od którego zależy, się skończą.

Po kilku miesiącach każdy z tych programistów będzie **ekspertem od swojego procesu** i będzie miał w nosie inne moduły - **SIC**!. (dzięki temu, że mógł się skupić na swojej robocie)

Jest jeszcze jedna kwestia.

Co na poziomie wszystkich modułów robi pakiet **infrastructure** i czym różni się od pakietu **infrastructure,** który jest wewnątrz modułów?

W tym module trzyma się rzeczy niezwiązane z domeną aplikacji. Są tam wszystkie implementacje potrzebne do funkcjonowania aplikacji.

Na przykład eventy, security, klienty http do innych serwisów, metryki, kolejki (są to rzeczy, które są niezbędne do działania aplikacji, ale nie są związane z żadnym konkretnym modułem). Zaraz zobaczysz przykłady tego co może być w **infrastructure**.

A **infrastructure** wewnątrz modułów przechowuje implementację infrastruktury dotyczącej **tylko tego modułu**, czyli na przykład:

-   Kontroler restowy **EmailSenderController,**
-   Implementację bazy Mongo **MongoDbEmailRepository** (do produkcyjnego wykorzystania, a także testów integracyjnych).
-   Implementację bazy danych w pamięci **InMemoryEmailRepository.** Gdy implementujesz bazę danych w pamięci **tylko pod** **testy jednostkowe** to rób to w pakiecie w **testach** (jak na obrazku powyżej)

Zaraz zobaczysz przykłady tego co może być w **infrastructure**.

Zobacz jak na poniższym schemacie może wyglądać moduł **emailsender**.

![Diagram
Description automatically generated](https://embed.filekitcdn.com/e/PnRL2gAKLh5sBLF3edZhT/kxq6NGKmcSLh3Jj5FJvJpJ)

Jeśli logika jest skomplikowana, to powinna zostać wydzielana do **osobnych** **klas**, a nie być trzymana w klasie **EmailFacade** (Fasada powinna być cienka).

![Graphical user interface, text, chat or text message
Description automatically generated](https://embed.filekitcdn.com/e/PnRL2gAKLh5sBLF3edZhT/dHapodCxUZpAanG24UyVTb)

W tym przypadku Fasada korzysta z klas **EmailSender** i **EmailRetriever**.

Dzięki temu kod klasy **EmailFacade** sprowadza się do wykorzystania tych klas.

A do tworzenia obiektów wykorzystujesz klasę EmailConfiguration.

![Text
Description automatically generated](https://embed.filekitcdn.com/e/PnRL2gAKLh5sBLF3edZhT/qbPDhRXXtm3if75BybAwYK)

Jeśli byśmy podpięli Springa pod to, to wtedy dodajemy andotacje **@Configuration** i **@Bean.** Dzięki czemu inne moduły mogą wstrzykiwać tę fasadę u siebie (więcej info [tutaj](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/x0hph6hn2n59m4i5/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj01UThraVNONjM5MA==)).

## 2. Moduł powinien zawierać wszystkie warstwy pionowe ([vertical layers](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/9qhzhnhgwgoz73c9/aHR0cHM6Ly9zdGVybnNjaGxldWRlci5kZS8yMDIxLzAxLzI4L2hvcml6b250YWwtYW5kLXZlcnRpY2FsLWxheWVycy1pbi1zb2Z0d2FyZS1kZXZlbG9wbWVudC8=))

Najwyższa warstwa **- API**

(umożliwia dostęp do modułu z zewnątrz)

Niższa warstwa **DOMENA.**

Klasy **Email**, **EmailRepository**, **EmailConfiguration** i kolejne klasy dotyczące wysyłania maili.

To jest domena aplikacja czyli zachcianki i funkcjonalności przychodzące z biznesu. (kod główny modułu)

Najniższa warstwa **Dane** - manipulowanie pamięcią  
(dane aplikacji)  
​  
WAŻNE: Nie rób tak, że robisz pakiet "**WOREK na wszystko"** na przykład:

-   pakiet o nazwie **controllers** i tam wrzucasz wszystkie kontrolery dostępne w aplikacji, albo
-   **facades** i tam wszystkie fasady.

To jest podejście **horyzontalne** i nie jest to często spotykana praktyka, można nawet powiedzieć, że jest to **antypattern**.

Rób pakiety, które mają wertykalne (pionowe) warstwy, a nie horyzontalne :)

## 3. Moduł ukrywa (enkapsuluje) swój **kod** i swoje **dane**.

Single Responsiblity Principle (literka S z [SOLID’a](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/08hwh9hmem3g8gcl/aHR0cHM6Ly9qYXZhcmVhZHkucGwvZGVtbw==)) na poziomie modułu powinno zostać zachowane.

Moduł odpowiada tylko za jeden proces i powinien zmieniać się tylko wtedy gdy zmiany dotyczą tego konkretnego procesu (np. tylko wysyłki maila lub tylko generacji pdfa).

Uwaga. To co zaraz przeczytasz o danych modułu może być nieintuicyjne.

Zdaję sobie z tego sprawę, dlatego możesz wrócić jeszcze raz do poniższej sekcji po przeczytaniu całego maila.

Moduł ma swoją własną bazę danych, do której żaden inny moduł nie powinien mieć dostępu!

Każdy moduł powinien mieć swoją tabelkę w bazie albo nawet osobną bazę danych. I nikt nie może nic w niej zmienić!

Tylko ten jeden moduł może manipulować swoimi danymi. To jest właśnie [enkapsulacja](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/z2hghnho6oqpgqap/aHR0cDovL29wcm9ncmFtb3dhbml1LnBsL2N6eW0tamVzdC1lbmthcHN1bGFjamEv) kodu i danych w module.

Mowa tutaj oczywiście o jednej aplikacji z wieloma modułami, a nie o mikroserwisach. W mikroserwisach naturalnym jest że każdy mikroserwis ma swoją własną bazę danych.

Nie opieraj swojej aplikacji wielomodułowej na jednej bazie danych*!

*baza danych jest tutaj tylko uproszczeniem - to wcale nie musi być jedna baza danych na jednej maszynie.

Izolacją może być to, że każdy moduł ma swoją tabelkę w bazie danych. Ale chodzi o to, żeby żaden inny moduł nie miał dostępu do tych danych bezpośrednio. Może tylko komunikować się przez API modułu!

Ale co jeśli każdy moduł będzie miał swoją “bazę danych”?

Co ze synchronizowaniem danych i duplikacjami?

Czy to nie zabije całego systemu, gdy kilka modułów potrzebuje przechowywać dokładnie te same dane?

To jest bardzo mylne podejście.

​

![Diagram
Description automatically generated](https://embed.filekitcdn.com/e/PnRL2gAKLh5sBLF3edZhT/dvcznhucG31brgsF14wXRW)

​[źródło](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/qvh8h7h8w89ng4cl/aHR0cDovL3d3dy5rYW1pbGdyenliZWsuY29tL3RhZy9zb2Z0d2FyZS1hcmNoaXRlY3R1cmUv)​

Na tym obrazku skup się na module "**module 1" data** i module "**module 3" data**.

Każdy z modułów ma swoje dane i nikomu nie chce ich bezpośrednio udostępniać (robi to przez metody swojego API).

Przecież ten obrazek reprezentuje wciąż **jedną** aplikację! To może być ta sama baza danych ale inne tabelki/kolekcje w bazie.

Jeśli cofniemy się o 30 lat, to wtedy trzymanie wszystkiego w jednej bazie i pozwolenie całej aplikacji oraz wszystkim jej modułom na **dowolne operacje na wszystkich danych** we wspólnej bazie **miało sens**.

To dlatego na studiach uczą [normalizować dane](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/48hvheh0l04gz0ax/aHR0cHM6Ly9kb2NwbGF5ZXIucGwvNTU2MjQ3OTAtTm9ybWFsaXphY2phLTFuZi0ybmYtM25mLWJjbmYtNG5mLTVuZi5odG1s) (zazwyczaj to, co jest na studiach jest minimum 10 lat do tyłu do tego co jest w komercyjnych projektach).

Są to stare praktyki, które pozwalają m.in na **optymalizacje wykorzystania pamięci** bazy danych.

**Nie było wtedy aż tyle pamięci,** by pozwolić na nadmiarowe duplikacje danych. Pamięć była po prostu droga i każde optymalizacje były mile widziane.

Ale na te czasy jest to antywzorzec.

Firmy takie jak Oracle czy IBM promują ten antywzorzec.

A wiesz, dlaczego tak jest?

Bo one sprzedają soft bazodanowy i wsparcie do ich baz :P

## 4. Moduł ma swoje API

Dostęp do modułu jest możliwy jedynie poprzez API, które wystawia na użytek innych modułów. A nie przez zaglądnięcie do jego bebechów.

Wszystkie klasy, interfejsy w module, oprócz API, powinno być ukryte i być prywatne (słówko private w Javie lub nie mieć żadnego słówka (wtedy jest dostępne tylko w obrębie pakietu Javowego - a taki moduł to właśnie może być pakiet)).

Komunikacja między modułami odbywa się tylko za pomocą ich klas API (często ta klasa to Fasada z publicznymi metodami).

## 5. Moduł ma kolaborantów (inne moduły, z którymi współpracuje)

Pojedynczy moduł sam w sobie może robić bardzo mało i nie być samowystarczalny. Na przykład w module od zamówień potrzebna jest informacja o tym czy użytkownik istnieje w bazie (moduł uwierzytelniania).

Często moduły komunikują się między sobą (mogą to robić tylko poprzez swoje API)

## 6. Moduł może być **kandydatem** na mikroserwis

Nie zawsze da się w łatwy sposób **wyciągnąć moduł do mikroserwisu.**

**Latency**

Dochodzi **opóźnienie** (latency) spowodowane połączeniem po sieci.**​  
​**Porównaj sobie **dwie aplikacje mikroserwisowe** (dwa osobne serwisy komunikujące się bezpośrednio po HTTP lub za pomocą eventów), z **jednym monolitem**, która zawiera **dwa moduły** (czyli dwa moduły w jednej aplikacji).**​  
​**Co będzie miało mniejsze opóźnienia z perspektywy użytkownika korzystającego z tych aplikacji? Oczywiście, że monolit.

**Tracisz transakcje**

W aplikacji monolitycznej jesteś w stanie utrzymywać transakcje bazodanowe między modułami, czyli dbać spójność danych w bazie (jeśli jedna operacja zawiedzie w transakcji to cała transakcja jest **rollbackowana**). Więcej o transakcjach w przyszłym mailu o bazach danych!

A jeśli wyciągniesz moduł do mikroserwisu to stracisz transakcje!**​  
​**(nie ma czegoś takiego jak rozproszona transakcja).**​  
​**W takim wypadku musisz się ratować **architekturą opartą o zdarzenia** lub **innymi wzorcami** (wspomnę o tym na końcu maila).

Zawsze przy tworzeniu nowego modułu upewnij się, czy **spełnia on powyższe zasady**.

Masz teraz zestaw narzędzi, żeby się upewnić, czy twój moduł jest dobry.

Obejrzyj koniecznie video w języki polskim o tym jak pakietować i dzielić na moduły:**​  
​**[**tutaj**](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/x0hph6hn2n59m4i5/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj01UThraVNONjM5MA==) (**gorąco polecam**).

A potem jeszcze zobacz **koniecznie** [**video**](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/08hwh9hmem3z0gil/aHR0cHM6Ly95b3V0dS5iZS9HRWpwX2pPVDJLNA==) o tym jak tworzyć dobre moduły od Sławka Sobótki.

Wiemy czym jest **moduł** więc możemy przejść do architektury **aplikacji**.

---

## Czym jest **architektura aplikacji**?

**Architektura aplikacji** to po prostu organizacja Twojego projektu, czyli:

1.  pakietowanie,
2.  nazewnictwo klas i pakietów,
3.  grupowanie w logiczne moduły,
4.  komunikacja między klasami i modułami.

Na tym etapie nie komplikuj sobie życia i naucz się tych najbardziej popularnych schematów w projektach komercyjnych.

Zacznij od **architektury warstwowej**, a potem przejdź do **heksagonalnej**.

Ale jeśli nauczysz się dobrze tylko warstwowej, to z pewnością do twoich prywatnych projektów to wystarczy.

(heksagon wprowadza dodatkową złożoność i niepoprawnie zastosowany może być tylko utrapieniem).

Ready? To lecimy!

## **Architektura Warstwowa**

Architekturę warstwową aplikacji możemy sprowadzić do **prostego podziału aplikacji na techniczne warstwy**.

Jego najpopularniejszą odmianą jest model **trójwarstwowy**.

Zobacz jak wygląda przykład z książki _Design IT!_

![Diagram
Description automatically generated](https://embed.filekitcdn.com/e/PnRL2gAKLh5sBLF3edZhT/mobtUvqx9YvZhxKQNH6SCc)

Najlepszym i najbardziej efektywnym co możesz zrobić, żeby poznać tę architekturę, jest skorzystanie z **gotowych materiałów w sieci.**

Mogę Ci polecić niedrogi [warsztat video](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/l2hehmho2o8r5qa6/aHR0cHM6Ly9rdXJzeS5udWxscG9pbnRlcmV4Y2VwdGlvbi5wbC9wcm9kdWN0L3dhcnN6dGF0LWFyY2hpdGVrdHVyYS13YXJzdHdvd2Ev) koszt ok. 50 zł (1h 30 min).

Po nim na pewno raz a dobrze poznasz praktykę i teorię na temat architektury warstwowej.

Bardzo ważną kwestią w kontekście architektury warstwowej i czymś, co musisz poznać jest też **mapowanie obiektów.**

Skoro warstwa niżej nie może wiedzieć nic o warstwie nad nią, to potrzebujemy stworzyć jakiś wspólny język międzywarstwowy, którym będą się komunikowały.

Jest to świetnie wytłumaczone w tym [video](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/7qh7h8h0l0rzv7iz/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj15eVp0eG5pV1dHTQ==).

**Polecane Darmowe Materiały (architektura warstwowa):**

1.  Architektura warstwowa – sposób na organizację kodu - [wpis](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/dpheh0hq6ql5zxbm/aHR0cHM6Ly9udWxscG9pbnRlcmV4Y2VwdGlvbi5wbC9hcmNoaXRla3R1cmEtd2Fyc3R3b3dhLXNwb3NvYi1uYS1vcmdhbml6YWNqZS1rb2R1Lw==)​
2.  Książka _Design IT_ - Rozdział 7: Warstwy.
3.  Architektura warstwowa - [wpis](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/p8heh9h969nx3dfq/aHR0cHM6Ly93d3cuYmRhYmVrLnBsL2FyY2hpdGVrdHVyYS13YXJzdHdvd2EtemxvLWN6eS1kb2Jyby8=) PL

Z dobrych praktyk korzystania z architektury warstwowej:

​

![Chart, box and whisker chart
Description automatically generated](https://embed.filekitcdn.com/e/PnRL2gAKLh5sBLF3edZhT/aYpwujsA26eHPUMUW52C44)

źródło [**DNA**](https://click.convertkit-mail2.com/p9uv0ogwxpaqumr3o5iq/qvh8h7h8w89n7dtl/aHR0cHM6Ly9kcm9nYW5vd29jemVzbmVnb2FyY2hpdGVrdGEucGwv)​

Powinno się stosować taką architekturę wzdłuż wartstw, ale per moduł.

Żeby nie doprowadzić do sytuacji, że powiedzmy **moduł z kontrolerem REST,** który pokazuje liczbę zalogowanych użytkowników w warstwie **prezentacji** korzysta **bezpośrednio z dwóch różnych modułów** w warstwie logiki biznesowej np. obliczenie liczby użytkowników online oraz wydrukowanie 1000 kartek świątecznych dla klientów.

Drukowanie kartek to jest totalnie **inny moduł** i warstwa prezentacji powinna mieć osobny moduł z kontrolerem do akcji na tym module.

Wtedy łatwiej utrzymać taką aplikację w architekturze warstwowej.

Oki to tyle, przejdź do materiałów lub idź dalej...

**Warstwy** za nami, teraz **heksagon**!

## **Architektura Heksagonalna (inaczej architektura portów i adapterów)**

Architektura heksagonalna ma na celu stworzenie **luźno powiązanych komponentów aplikacji**, które można łatwo **połączyć za pomocą portów i adapterów**. To sprawia, że komponenty są **wymienialne** na każdym poziomie i ułatwia automatyzację testów.

![Diagram
Description automatically generated](https://embed.filekitcdn.com/e/PnRL2gAKLh5sBLF3edZhT/5ZdCGm5rgCYuNk9NrHua5J)

W rzeczywistości **nie warto jej stosować do prostych aplikacji**.

Najczęściej stosuje się ją w aplikacjach związanych z integracjami różnych systemów.

Na przykład: kilka banków i ich API do płatności, kilka baz danych z różnych powodów mongodb, mysql.