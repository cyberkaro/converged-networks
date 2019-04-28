# RSVP (Resource reSerVation Protocol) Protokół rezerwacji zasobów #


**RSVP** jest wykorzystywany przez hosty do żądania określonej jakości usługi QoS od sieci dla konkretnego strumienia danych (stream) lub przepływu (flow) aplikacji. Jest również stosowany przez routery do dostarczania żądań jakości usług QoS do wszystkich węzłów na ścieżce danego przepływu i ustanawiania oraz utrzymywania stanu dla dostarczenia żądanej usługi.
 
Żądania RSVP (Resource Reservation Protocol) skutkują ogólnie zarezerwowaniem określonych zasobów w każdym węźle wzdłuż ścieżki danych. RSVP żąda zasobów dla pojedynczego kierunku strumienia (simplex). traktuje nadawcę logicznie oddzielnie niż odbiorcę pomimo, że ten sam proces aplikacji może w tym samym czasie działać zarówno jako nadawca jak i odbiorca. Protokół działa na szczycie IPv4 i IPv6, zajmując miejsce protokołu transportowego w stosie protokołów. Jednak RSVP nie przenosi danych aplikacji, ale jest raczej internetowym protokołem sterowania, jak ICMP, IGMP lub protokoły routingu. Tak jak implementacja protokołów zarządzania i routingu, implementacja RSVP jest typowo wykonywana w tle, a nie w ścieżce przekazywania danych.
  
# Model działania RSVP #
RSVP nie jest sam w sobie protokołem routingu, jest zaprojektowany do działania z bieżącymi i przyszłymi unicastowymi i multicastowymi protokołami routingu. Proces RSVP odpytuje lokalną bazę danych routingu w celu uzyskania trasy. W przypadku multicastu, host wysyła wiadomość IGMP, aby przyłączyć się do grupy multicastowej a następnie wysyła wiadomość RSVP by zarezerwować zasoby wzdłuż ścieżki dostarczającej informacje tej grupie. Protokoły routingu określają, gdzie pakiety zostaną przekazane, natomiast RSVP jest tylko zainteresowany jakością usług QoS dla tych pakietów, które są przekazywane zgodnie z routingiem.

Jakość usług jest implementowana dla konkretnego strumienia danych przez mechanizmy nazywane sterowaniem ruchu (traffic controll). Mechanizmy te zawierają klasyfikator pakietów, sterowanie dostępem i szeregowanie pakietów lub inne mechanizmy zależne od warstwy łącza danych, które określają, kiedy konkretny pakiet zostanie przekazany. Klasyfikator pakietów wyznacza klasę QoS dla każdego pakietu. Dla każdego interfejsu wychodzącego, mechanizm szeregowania pakietów osiąga obiecanych parametrów QoS. Sterowanie ruchem implementuje w ten sposób model usług QoS zdefiniowany przez grupę roboczą Integrated Services Working Group.

W czasie zestawiania rezerwacji zasobów, żądanie QoS RSVP jest przekazywane do dwóch lokalnych modułów decyzyjnych: sterowania dostępem i sterowania polityk. Sterowanie dostępem określa czy węzeł ma wystarczająco dostępnych zasobów do zapewnienia żądanych QoS. Sterowanie polityk określa czy użytkownik ma administracyjne uprawnienia do realizacji rezerwacji. Jeśli oba sprawdzenia będą pozytywne, to parametry zostaną ustawione w klasyfikatorze pakietów i interfejsie warstwy łącza danych by uzyskać pożądane QoS. Jeśli sprawdzenia będą negatywne, RSVP zwraca informacje o błędzie do procesu aplikacji, która zapoczątkowała żądanie.

Architektura RSVP zakłada, że poszczególne stany i sterowania ruchem są budowane i niszczone przyrostowo w routerach i hostach. W tym celu RSVP jest protokołem typu soft state, co oznacza, że wysyła okresowo wiadomości odświeżające by utrzymywać stany wzdłuż zarezerwowanej ścieżki. W przypadku braku wiadomości odświeżającej, stan ulega automatycznemu przeterminowaniu i jest kasowany.

Podsumowując RSVP (Resource Reservation Protocol) ma następujące cechy:
*	Tworzy rezerwację dla aplikacji unikastowych i multicastowych, adaptując się dynamicznie do zmian w członkostwie grupy, jak i zmian w trasach;
*	Jest simpleksowy- robi rezerwację dla jednokierunkowego strumienia danych;
*	Jest zorientowany na odbiornik- odbiornik strumienia danych inicjuje i utrzymuje rezerwacją zasobów wykorzystywaną dla tego strumienia; 
*	Utrzymuje stany „soft” w routerach i hostach, wprowadzając wsparcie dla dynamicznych zmian członkostwa i automatycznej adaptacji do zmian routingu;
*	Nie jest protokołem routingu, ale jest zależny od protokołów routingu;
*	Transportuje i utrzymuje parametry sterowania ruchem (traffic control) i sterowania polityk (policy control), które są nieprzeźroczyste dla RSVP;
*	Udostępnia kilka modeli rezerwacji lub tzw. stylów rezerwacji, by dopasować się do aplikacji;
*	Działa transparentnie dla routerów, które go nie obsługują;
*	Obsługuje zarówno IPv4 jak i IPv6.



### Źródła
[Źródło pierwsze](http://www.tech-portal.pl/content/view/62/45/)
[Źródło drugie](https://pl.wikipedia.org/wiki/Resource_Reservation_Protocol)
[Źródło trzecie](https://pl.wikipedia.org/wiki/Quality_of_service)


> Dawid Stawski
