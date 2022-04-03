https://dbadmin.net.pl/podstawy-postgresql-dla-administratora/

**postgresql.conf**
Sprawdź aktualny adres nasłuchu PostgreSQL:
``[postgres@postgres-lab ~]$ netstat -lptnu | grep post 
(Not all processes could be identified, non-owned process info will not be shown, you would have to be root to see it all.) 
tcp 0 0 127.0.0.1:5432 0.0.0.0:* LISTEN 1977/postmaster 
tcp6 0 0 ::1:5432 :::* LISTEN 1977/postmaster`


Zmień w `postgresql.conf` parametr `listen_addresses` na adres Twojego serwera bazodanowego, lub na '*’ w celu nasłuchu na wszystkich dostępnych adresach.

## Konfiguracja dostępu zdalnego – pg_hba.conf
-   `local` – socket connection – połączenie lokalne z shell serwera bazodanowego
-   `host` – standardowe połączenie TCP/IP poprzez sieć
-   `hostssl` – połączenie TCP/IP tylko z SSL
-   `hostnossl` – przeciwieństwo poprzedniego czyli, tylko bez SSL
-   `hostgssenc` – TCP/IP tylko z GSSAPI
-   `hostnogssenc` – TCP/IP tylko bez GSSAPI
- 

W kolumnie `DATABASE` możemy podać nazwę bazy danych, lub użyć specjalnej wartości `sameuser`. Wartość ta zakłada że wpis jest dla bazy danych o dokładnie takiej nazwie jak nazwa użytkownika, który się łączy.

Kolumna `USER` przyjmuje nazwę użytkownika albo roli. Przy nazwie roli musimy przed nią dopisać jeszcze znak „+”.

Pole `ADDRESS` to nic innego jak hostname lub zakres IP w formacie CIDR.
-   `samehost` – wszystkie adresy na serwerze bazodanowym
-   `samenet` – wszystkie adresy IP w podsieci serwera bazodanowego

Pole `METHOD` pozwala wybrać metodę uwierzytelniania
-   `trust` – pozwala na połączenie nie bez podawania hasła – głownie ustawiane dla sesji shell na serwerze bazodanowym
-   `reject` – odrzucanie połączeń
-   `md5` – pozwala na połączenie po otrzymaniu hasła – haszowane hasła
-   `password` – pozwala na połączenie po otrzymaniu hasła – NIE UŻYWAĆ! – hasła przesyłane  „plain text”
-   `ldap` – pobieranie informacji o kontach i uwierzytelnianiu z LDAP