* Table of contents
{:toc}

___
# 1. Wstêp  

# 2. Systemy lokalizacyjne UWB

## 2.1. Sygna³y UWB 

### 2.1.1. Charakterystyka
UWB (Ultra Wide Band) to technologia umo¿liwiaj¹ca przesy³anie sygna³ów radiowych o bardzo du¿ej szerokoœci pasma. Wed³ug norm FCC (Federal Communications Commission) sygna³ ultraszerokopasmowy posiada wzglêdn¹ szerokoœæ pasma (okreœlon¹ jako pasmo 10dB spadku od poziomu sk³adowej o czêstotliwoœci œrodkowej) wiêksz¹ od 20% lub bezwzglêdn¹ szerokoœæ pasma wiêksz¹ od 500MHz. W Europie, gdzie organem reguluj¹cym jest Komisja Europejska, sygna³em ultraszerokopasmowym nazywamy taki, którego bezwglêdna szerokoœæ pasma jest wiêksza ju¿ od 50MHz.

Zgodnie z twierdzeniem Shannona maksymalna mo¿liwa do osi¹gniêcia przep³ywnoœæ transmisji informacji jest wprost proporcjonalna do bezwzglêdnej szerokoœci pasma sygna³u. W zwi¹zku z tym sygna³y UWB maj¹ potencjalnie bardzo du¿e mo¿liwoœci z punktu widzenia przesy³ania strumieni danych o du¿ej przep³ywnoœci. Dodaktowo szerokie pasmo umo¿liwia ograniczenie mocy nadawanego sygna³u, dziêki czemu urz¹dzania wykorzystuj¹ce UWB do transmisji radiowej bêd¹ bardziej energooszczêdne. Dziêki impulsowej pracy i niewielkim mocom sygna³ów systemy te mog¹ pracowaæ w zajêtych ju¿ pasmach bêd¹c praktycznie niewykrywalne przez osoby postronne.

Transmisja radiowa wykorzystuj¹ca UWB ma przed sob¹ ciekaw¹ przysz³oœæ. Dzisiejsze mobilne systemy s¹ coraz bardziej miniaturyzowane i narzucane s¹ na nie wysokie wymagania dotycz¹ce zu¿ycia energii. Ponadto urz¹dzania staj¹ siê coraz bardziej multimedialne, w zwi¹zku z czym rosn¹ oczekiwania co do obs³ugiwanych przep³ywnoœci strumieni danych. Wprowadzenie systemów UWB do transmisji danych na pewno u³atwi producentom sprzêtu spe³nienie rosn¹cych wymagañ.

### 2.1.2. Propagacja

## 2.2. Systemy TDOA
Systemy lokalizacyjne jeszcze do niedawna kojarzy³y siê g³ównie z lotniczymi i wojskowymi radarami. W dzisiejszych czasach lokalizacja urz¹dzeñ coraz œmielej wkracza w ró¿ne dziedziny ¿ycia bliskie ka¿emu cz³owiekowi. Dobrym tego przyk³adem tego zjawiska jest telefonia komórkowa, której operatorzy s¹ zobligowani do wprowadzenia technicznych rozwi¹zañ umo¿liwiaj¹cych odpowiednim s³u¿bom lokalizacjê terminala. Pojawiaj¹ siê tak¿e systemy, których celem jest okreœlenie dok³adnej pozycji i przemieszczenia danego czujnika wewn¹trz budynku lub pojedynczego pomieszczenia.
Opracowano wiele technik i modeli matematycznych umo¿liwiaj¹cych okreœlenie pozycji w ró¿nych warunkach. Do najbardziej popularnych metod nale¿¹:

* RSS (Recieved Signal Strenght) - oparta na pomiarze poziomu mocu sygna³u,
* AOA (Angle of Arrival) - oparata na pomiarze k¹ta nadejœcia sygna³u,
* TOA (Time of Arrival) - oparta na pomiarze czasu propagacji sygna³ów w ³¹czu radiowym
* TDOA (Time Difference of Arrival) - oparta na pomiarze ró¿nicy czasów propoagacji sygna³ów w ³¹czu radiowym.

Z punktu widzenia omawianej pracy najistotniejsze jest omówienie ostatniej z wymienionych metod, czyli TDOA. Opiera siê ona na wyznaczeniu odstêpów czasowych pomiêdzy sygna³ami docieraj¹cymi z ró¿nych wêz³ów sieci. Na podstawie tych parametrów mo¿na obliczyæ po³o¿enie, które wypada na przeciêciu odpowiednik hiberboli (w przestrzeni dwuwymiarowej) lub hiberboloid (w przestrzeni trójwymiarowej).

`rysunek`

Niew¹tpliw¹ zalet¹ systemu TDOA jest brak koniecznoœci synchronizacji zegarów odbiornika z wêz³ami referencyjnymi, gdy¿ istotne s¹ tylko ró¿nice w czasie docieraj¹cych sygna³ów. Nie ma zatem koniecznoœci stosowania bardziej wyrafinowanych metod umo¿liwiaj¹cych dok³adn¹ synchronizacjê. 

Istniej¹ dwa warianty omawianej metody. W pierwszej z nich sygna³y nadawane s¹ od wêz³ów referencyjnych w stronê obiektu lokalizowanego, który jest odbiornikiem. Umo¿liwia to lokalizowanie jednoczesne wielu urz¹dzeñ bêd¹cych w oszarze dzia³ania systemu, jednak¿e komplikuje to budowê odbiornika, w którym nale¿y zaimplementowaæ algorytmy obliczaj¹ce pozycjê. W drugiej wersji to lokalizowane urz¹dzenie jest nadajnikiem, a wêz³y referencyjne odbieraj¹ sygna³. Zalet¹ tego rozwi¹zania jest uproszczenie urz¹dzenia lokalizowanego i przeniesienie bloku obliczaj¹cego pozycjê do jednego z wêz³ów. Taki system wymaga jednak wprowadzenia mechanizmu wielodostêpu, aby móc lokalizowaæ kilka urz¹dzeñ na raz. 

`Krótkie impulsy umo¿liwiaj¹ precyzyjne okreœlenie po³o¿enia`

## 2.3. System opracowany w PMR przez mgr Kosiñskiego (tytu³ roboczy)

### 2.3.1. Architektura

Opracowany i opisany w `bibl:praca p.Kosiñskiego` system sk³ada siê z z piêciu nadajników (uk³ad cyfrowy CPLD, generator UWB oraz antena) po³¹czonych szeregowo (struktura zosta³a przedstawiona na `rys 2.1`). Pierwszy z nich jest nadajnikiem nadrzêdnym, który:

* decyduje o rozpoczêciu procesu generacji i wysy³aniu impulsów w ³¹czu radiowym,
* uruchamia kolejny nadajnik,
* jest Ÿród³em sygna³u zegarowego.

Ka¿dy z kolejnych nadajników otrzymuje sygna³ zegara oraz sygna³ wyzwalaj¹cy. Zegar jest regenerowany i wysy³any dalej, po czym jest u¿ywany jako lokalny sygna³ zegarowy, dziêki czemu wszystkie nadajniki s¹ ze sob¹ zsynchronizowane. Po otrzymaniu sekwencji steruj¹cej, ka¿dy nadajnik wysy³a impulsy w ³¹czu radiowym, które steruj¹ prac¹ odbiornika. Odpowiednie sekwencje uruchamiaj¹ i zatrzymuj¹ pomiar czasu, a tak¿e nios¹ treœæ informacyjn¹ umo¿liwiaj¹c¹ zidentyfikowanie konretnego nadajnika. Odbiornik, zgodnie ze sposobem dzia³ania systemów typu TDOA, mierzy ró¿nicê czasów pomiêdzy otrzymaniem sygna³ów z poszczególnych nadajników. Po wys³aniu sekwencji z ostatniego nadajnika pomiar siê koñczy i odbiornik przechodzi do obliczania pozycji korzystaj¹c z zaprogramowanych algorytmów.

![Schemat uk³adu ](./img/kosinski.png "img:Rys2.1")

### 2.3.2. Sygna³y w ³¹czu radiowym

W ³¹czu radiowym systemu nadawane by³y pakiety o strukturze przedstawionej na rysunku `rys 2.2`.

![Uproszczony schemat sygna³ów w ³¹czu radiowym ](./img/kosinski_sygnaly.png "Rys2.2")

Preambu³a umo¿liwia wysterowanie uk³adu automatycznej regulacji wzmocnienia. Nastêpnie przesy³ana jest komenda STOP, która zatrzymuje pomiar czasu. Bity identyfikatora umo¿liwiaj¹ odbiornikowi rozpoznanie Ÿród³a przesy³anego sygna³u. Pakiet koñczy komenda uruchomiaj¹ca pomiar.

# 3. Systemy Cyfrowe

## 3.1. Klasyczne Systemy Cyfrowe
Koniec ubieg³ego wieku przyniós³ niesamowity rozwój systemów elektronicznych. Odst¹piono od elektroniki analogowej i zaczêto projektowaæ oraz produkowaæ na masow¹ skalê uk³ady cyfrowe. W fazie projektowania wykorzystywano mechanizmy oparte na algebrze Boola - tworzono opis uk³adu w postaci tablicy prawdy, któr¹ za pomoc¹ ró¿norodnych technik optymalizacyjnych (tablice Karnough'a, dekompozycja) sprowadzano do postaci równania boolowskiego. Nastêpnie tworzono realizacjê równañ przy pomocy bramek logicznych, przerzutników, liczników, rejestrów, uk³adów arytmetycznych itd. Fizyczn¹ postaæ tworzono najczêœciej wykorzystuj¹c uk³adów scalonych firmy Texas Instruments z serii TTL 74xx, które dostarcza³y gotowe implementacje wiêkszoœci podstawowych struktur logicznych. W trakcie budowania systemu w rol¹ konstruktora by³o odpowiednie poprowadzenie œcie¿ek miêdzy wejœciami i wyjœciami uk³adów.

![Fazy projektowania (Ÿród³o bibl:VHDL ](./img/fazy_projektowania.png "img:Rys3.1")

Rozwój systemów poci¹gn¹³ za sob¹ znaczne skomplikowanie uk³adów cyfrowych, co spowodowa³o ¿e dotychczasowe metody przesta³y byæ wystarczaj¹ce. D³ugi czas projektowania i z³o¿one prototypowanie uniemo¿liwa³o szybkie tworzenie nowego sprzêtu. W poszukiwaniu nowych mo¿liwoœci realizacji elektroniki cyfrowej wynaleziono uk³ady programowalne.

## 3.2. Uk³ady logiki programowalnej
Pierwsze uk³ady logiki programowalnej to tzw. uk³ady PAL (*Programmable Array Logic*). Ich wewnêtrzna budowa sk³ada³a siê z matrycy bramek AND oraz matrycy bramek OR, gdzie matryca iloczynów by³a programowalna, natomiast matryca OR - po³¹czona na sta³e. 

![Struktura PAL](./img/pal.png "img:Rys3.2")

Dowolne kombinacje po³¹czeñ wewn¹trz struktury umo¿liwia³y realizacjê bardziej skomplikowanych funkcji w ³atwiejszy sposób. Po raz pierwszy wykorzystano oprogramowanie komputerowe typu CAD (*Computer Aided Design*), które wspomaga³o projektanta w trakcie tworzenia uk³adu. Zmieni³o siê podejœcie do samego procesu projektowania.

![Fazy projektowania (Ÿród³o bibl:VHDL) ](./img/fazy_projektowania_cpld.png "img:Rys3.3")

Konstruktor nie musia³ samemu realizowaæ po³¹czeñ miêdzy bramkami, gdy¿ zajmowa³o siê tym oprogramowanie, które dostarcza³o gotow¹ "mapê przepaleñ" po³¹czeñ wewnêtrzych uk³adu PAL.

Wykorzystanie uk³adów logiki programowalnej mia³o wiele zalet. Przede wszystkim uwolni³o projektanta od koniecznoœci schodzenia do poziomu bramek logicznych, gdy¿ zajmowa³o siê tym oprogramowanie. System wymagaj¹cy wielu modu³ów TTL móg³ sk³adaæ siê z jednego uk³adu scalonego realizuj¹cego tê sam¹ funkcjê pracuj¹c szybciej. Ograniczono pobór energii oraz wymagane miejsce na p³ytce. 

Wzglêdy ekonomiczne równie¿ przemawia³y za uk³adami PAL. Projekty mog³y byæ realizowane i weryfikowane znacznie szybciej, co ogranicza³o koszty. Dziêki elastycznoœci tych modu³ów zmiany w dzia³aniu systemu wymaga³y tylko zmiany "mapy przepaleñ", natomiast sama p³ytka drukowana pozostawa³a bez zmian. Mo¿liwe by³o stworzenie uniwersalnych p³ytek ewaluacyjnych umo¿liwiaj¹cych ³atwe prototypowanie uk³adu. 

## 3.3. Uk³ady CPLD	
Kolejnym krokiem w rozwoju programowalnych struktur logicznych by³o pojawienie siê uk³adów typu CPLD (*Complex Programmable Logic Device*). Ich struktura sk³ada siê z zestawu bloków logicznych wraz z czêœci¹ odpowiedzialn¹ za po³¹czenia wewnêtrzne. Ka¿dy z bloków sk³ada siê z:

* matrycy elementów iloczynowych,
* bloku sumy logicznej,
* makrokomórek.

`schematy, s59`

Blok odpowiedzialny za po³¹czenia programowalne mo¿e byæ realizowany na dwa sposoby:

1. po³¹czenia oparte na matrycy, gdzie wyjœcia ka¿dego z bloków ³¹czone jest do matrycy poprzez element pamiêtaj¹cy (komórka EPROM); ponadto istnieje mo¿liwoœæ zrealizowania wszystkich po³¹czeñ, tj. dowolne wejœcie mo¿e byæ po³¹czone z dowolnym blokiem logicznym.
1. po³¹czenia oparte na multiplekserze, gdzie ka¿demu wejœciu bloku logicznego odpowiada jeden multiplekser, a linie adresuj¹ce s¹ programowane tak, aby zapewniæ odpowiednie po³¹czenia.

Bloki logiczne swoj¹ struktur¹ przypominaj¹ uk³ady typu PAL.  Bloki te zawieraj¹ zwykle od 4 do 20 makrokomórek, przy czym wystarczy ich 16 aby realizowaæ szesnastobitowe funkcje logiczne w jednym bloku.

Makrokomórki sk³adaj¹ siê z przerzutników oraz uk³adów sterowania polaryzacj¹, dziêki czemu mo¿na realizowaæ zarówno funkcje proste jak i zanegowane. Dodatkowo uk³ad CPLD czêsto posiada makrokomórki we/wy, które stanowi¹ bufor i zabezpieczenie w interfejsie I/O.

Uk³ady CPLD posiadaj¹ równie¿ inne, ciekawe w³asnoœci. Oferuj¹ czêsto konstruktorowi standard ISP (*In System Programmability*), który umo¿liwia programowania uk³adu bezpoœrednio w systemie bez koniecznoœci umieszczania elementu w programatorze. Dodatkowo, nowsze uk³adu implementuj¹ standard JTAG, który umo¿liwia debuggowanie i testowanie uk³adu pracuj¹cego w systemie.

## 3.4. Uk³ady FPGA

**Field Programmable Gate Array** to aktualnie najbardziej rozwiniêty rodzaj programowalnych uk³adów logicznych, który umo¿liwia realizacjê bardzo z³o¿onych struktur. Posiada mo¿liwoœci identyczne z uk³adami typu ASIC (Application-Specific Integrated Circuit - zintegrowane uk³ady projektowane do zastosowania w konkretnym systemie), dla których czêsto stanowi prototyp. Mimo i¿ uk³ady FPGA s¹ zazwyczaj wolniejsze i pobieraj¹ wiêcej mocy mo¿na je wykorzystywaæ w wielu aplikacjach jako rozwi¹zanie ostateczne. Na ich rzecz przemawia krótszy czas projektowania oraz ni¿sze koszty produkcji.

![Matryca FPGA (Ÿród³o bibl:VHDL) ](./img/fpga.png "img:Rys3.5")

Wewnêtrzna struktura typowego uk³adu FPGA zosta³a przedstawiona na rysunku 3.3. Mo¿emy na niej wyró¿niæ:

* bloki wejœcia/wyjœcia,
* bloki logiczne,
* po³¹czenia programowalne.

Bloki logiczne wraz z programowalnymi po³¹czeniami stanowi¹ o ogromnych mo¿liwoœciach uk³adów FPGA. Ka¿dy z bloków umo¿liwia realizacjê dowolnej funkcji boolowskiej czterech argumentów. Ich wewnêtrzna struktura zosta³a przedstawiona na rysunku 3.6 i sk³ada siê z:

![Zarys pojedynczej komórki logicznej (Ÿród³o bibl:VHDL) ](./img/fpga_LB.png "img:Rys3.6")

* tablicy typu LUT (*Look Up Table*),
* sumatora,
* przerzutnika typu D.

Tablica LUT realizujê obs³ugê logiki. W jej strukturze zapisana jest tablica prawdy, do której w trakcie implementacji zosta³o sprowadzone równanie boolowskie lub opis w jêzyki HDL. Przerzutnik umo¿liwia synchronizacjê sygna³u wyjœciowego z dostarczonym sygna³em zegarowym. Za pomoc¹ multipleksera natomiast mo¿na decydowaæ czy odpowiedŸ na wyjœciu ma byæ synchroniczna czy asynchroniczna. 

Przy projektowaniu uk³adów typu FPGA konstruktor mo¿e tworzyæ aplikacjê na jeszcze wy¿szym poziomie abstrakcji - tj. wy¿szym ni¿ bramki logiczne i równania boolowskie. Wykorzystuje siê w tym celu jêzyki opisu sprzêtu HDL (*Hardware Description Language*, np. *VHDL*, *Verilog*, *AHDL*). Do zaprogramowania konfiguracji FPGA nale¿y wykorzystaæ œrodowisko dostarczone przez konkretnego dostawcê uk³adu (np. Xilinx - ISE Web Pack, Altera - Quartus). 

### Xilinx Spartan3
Na rynku powszechnie dostêpne s¹ uk³ady wielu producentów. Do najbardziej znacz¹cych nale¿¹ Altera i Xilinx. Realizacja omawianej pracy zosta³a oparta na uk³adzie Xilinx Spartan3 XC3S200. Posiada on 4 320 komórek logicznych, co jest odpowiednikiem ok. 200 000 bramek logicznych. Jego struktura jest rozszerzon¹ wersj¹ omówionej wczeœniej koncepcji i zosta³a przedstawiona na rysunku 3.7.

![Architektura uk³adu FPGA Xilinx Spartn3 XC3S200 (Ÿród³o bibl:spartan ](./img/spartan3.png "img:Rys3.7")

Poza podstawowymi elementami, którym s¹ bloki logiczne, mo¿emy wyró¿niæ tak¿e pamiêc typu RAM (sk³adaj¹ca siê z bloków po 18 kilobitów) oraz blok DCM (Digital Clock Manager), który dostarcza wszystkich funkcji niezbêdnych z dystrybucj¹ sygna³u zegarowego oraz operacjach z nim zwi¹zanych. Uk³ad posiada 173 linie wejœcia/wyjœcia, które umo¿liwiaj¹ wspó³pracê z sygna³ami przesy³anymi w ró¿nych standardach zarówno asymetrycznych (np. LVCMOS) jak i symetrycznych (np. LVDS).

## 3.5. Jêzyk VHDL
Tworzenie skomplikowanych systemów cyfrowych wymaga wykorzytania odpowiednich narzêdzi. Opis uk³adu w postaci równañ boolowskich jest trudny zarówno dla projektanta jak i osoby, która póŸniej mo¿e system rozwijaæ. Jêzyki opisu sprzêtu umo¿liwiaj¹ stworzenie opisu dzia³ania uk³adu na ró¿nych poziomach abstrakcji, dziêki czemu s¹ bardziej elastyczne i pozwalaj¹ szybciej tworzyæ skomplikowane struktury. Jednym z dwóch czo³owych jêzyków tego typu, obok jêzyka Verilog, jest VHDL (**V**ery-High-Speed Integrated Circuit **H**ardware **D**escription **L**anguage*), który zosta³ wykorzystany do realizacji projektu w ramach pracy dyplomowej.

Jêzyk ten zawiera u¿yteczne konstrukcje semantyczne, umo¿liwiaj¹ce tworzenie jasnego i czytelnego kodu reprezentuj¹cego uk³ad logiczny. Projekt mo¿e byæ opisany na wielu poziomach abstrakcji, dziêki czemu programista ma du¿¹ swobodê i elastycznoœæ w tworzeniu konfiguracji FPGA. Jêzyk umo¿liwia kreowanie i ³adowanie zewnêtrznych bibliotek, a tak¿e realizacjê modu³ów, które mog¹ byæ wielokrotnie wykorzystywane w projekcie (struktura hierarchiczna). Wiêkszoœæ instrukcji wykonywana jest równolegle, jednak¿e istniej¹ sposoby na stworzenie kodu wykonywanego sekwencyjnie (tzw. procedury) wraz z instrukcjami warunkowymi i pêtlami znanymi z klasycznych jêzyków programowania.

Du¿¹ zalet¹ tej technologii jest uniezale¿nienie opisu uk³adu od wyboru konkretnego uk³adu, w jakim bêdzie on póŸniej realizowany. Dziêki przenoœnoœci istnieje mo¿liwoœæ symulowania i testowania projektu w wielu œrodowiskach, co u³atwia znalezienie potencjalnych b³êdów. Uk³ad mo¿na poddaæ syntezie tak¿e w dowolnym œrodowisku do projektowania FPGA.

Niestety, mo¿liwoœæ tworzenia projektu na wysokim poziomie abstrakcji niesie za sob¹ pewne konsekwencja. Narzêdzia do syntezy czasem tworz¹ nieoptymaln¹ implementacjê. Jest to czêsto win¹ samego projektanta, który tworzy kod niezgodny z przyjêtymi konwecjami. Co wiêcej, niedoœwiadczony programista mo¿e napisaæ kod, który w ogóle nie jest syntezowalny. Z drugiej strony - sama idea tworzenia uk³adu cyfrowego na podstawie opisu w jêzyku HDL powoduje przyjêcie pewnych standardów przez kompilator i generowanie nieoptymalnych rozwi¹zañ w przypadku niecodziennych konstrukcji.

## 3.6. Implementacja 

Implementacja to pe³en proces stworzenia uk³adu cyfrowego odpowiadaj¹cego naszym oczekiwaniom. W jego wyniku otrzymujemy poprawn¹ konfiguracjê, któr¹ mo¿na zaprogramowaæ uk³ad FPGA i uruchomiæ w pe³ni dzia³aj¹ce urz¹dzenie. Poszczególne etapy implementacji to:

1. Zdefiniowanie za³o¿eñ i wymagañ projektowych,
1. Opisanie projektu w jêzyku typu *HDL*,
1. Symulacja kodu Ÿród³owego,
1. Synteza, optymalizacja i dopasowanie projektu,
1. Symulacja modelu dopasowanego i zrealzowanego projektu,
1. Zaprogramowanie uk³adu.

### 3.6.1. Zdefiniowanie za³o¿eñ i wymagañ projektowych
Ka¿dy projekt techniczny musi zacz¹æ siê od zdefniowania konkretnych za³o¿eñ. Nie inaczej jest w trakcie projektowania systemów cyfrowych. Nale¿y zdefiniowaæ wymagania, szczególnie dotycz¹ce:

* czêstotliwoœci dzia³ania uk³adu,
* czasów ustawiania i propagacji sygna³ów,
* œcie¿ek krytycznych.

Jasne sprecyzowanie wymagañ u³atwia dobór narzêdzi oraz konkretnych uk³adów, w których projekt zostanie zaimplementowany.

### 3.6.2. Opisanie projektu w jêzyku typu *HDL*
Zalecane s¹ 3 metody projektowania:

* zstêpuj¹ca (top-down),
* wstêpuj¹ca (bottom-up),
* pozioma.

W omawianym projekcie zosta³a wykorzystana pierwsza z nich. Polega na podzieleniu projektu na funkcje sk³adowe, maj¹ce okreœlone, specyficzne wejœcia i wyjœcia oraz realizuj¹ce odpowienie funkcje. Modu³ na najwy¿szym stopniu hierarchii spaja wszystkie elementy i umo¿liwia ³atw¹ analizê dzia³ania uk³adu. Takie podejœcie jest szczególnie korzystne przy tworzeniu skomplikowanych systemów. Oprogramowanie do projektowania uk³adów FPGA umo¿liwia realizacjê wielopoziomowych struktur.

Po stworzeniu bloków sk³adowych projektu nale¿y przejœæ do zakodowania funkcjonalnoœci ka¿dego z nich. 

### 3.6.3. Symulacja kodu Ÿród³owego
Œrodowiska do projektowania umo¿liwiaj¹ przeniesienie fazy symulacji i testowania do wczesnych etapów tworzenia systemu. Jest to tzw. "symulacja behawioralna", która obrazuje zachowanie uk³adu opisanego jêzykiem HDL bez uwzglêdnienia wp³ywu syntezy oraz poprowadzenia po³¹czeñ. Mo¿na zaobserwowaæ podstawowe zachowanie zrealizowanego projektu, jednak¿e bez tak kluczowych czynników, jak np. opóŸnienia i czasy propagacji.

### 3.6.4. Synteza, optymalizacja i dopasowanie projektu
#### Synteza 
Synteza to proces, w wyniku którego z abstrakcyjnego kodu HDL tworzona jest lista po³¹czeñ miêdzy blokami realizuj¹cymi odpowiednie funkcje logiczne lub zbiór równañ boolowskich. Rezultat tej operacji jest zale¿ny od konkretnej technologii, gdy¿ powinien byæ dopasowany do konkretnego modelu uk³adu FPGA, w którym projekt bêdzie implementowany. 

#### Optymalizacja
Proces optymalizacji jest zale¿ny od trzech czynników:

* postaci wyra¿eñ boolowskich,
* rodzaju dostêpnych zasobów sprzêtowych,
* ograniczeñ projektowych (**ang. constraints**).

Narzêdzia do optymalizacji umo¿lwiaj¹ wykorzystanie specyficznych w³aœciowœci uk³adu konkretnego producenta w celu zapewnienia najlepszych parametrów wynikowego projektu. Aby tego dokonaæ mog¹ korzystaæ z przekszta³ceñ równañ boolowskich otrzymanych w wyniku syntezy, aby dokonaæ optymalnej realizacji. Ograniczenia projektowe narzucone przez u¿ytkownika lub wprowadzone automatycznie umo¿liwiaj¹ efektywniejsz¹ optymalizacjê pod k¹tem wykorzystania dostêpnych zasobów.

#### Rozmieszczenie i poprowadzenie po³¹czeñ
Proces ten ma ogromny wp³yw na jakoœæ zrealizowanego uk³adu. Bardzo istotnym parametrem jest czas propagacji sygna³ów, na który kluczowy wp³yw ma sposób poprowadzenia po³¹czeñ, gdy¿ to one w³aœnie wprowadzaj¹ najwiêksze opóŸnienia. Programy najwy¿szej klasy umo¿liwiaj¹ wykorzystanie bloków logicznych le¿¹cych blisko siebie, dziêki czemu œcie¿ki po³¹czeniowe s¹ bardzo krótkie - w szczególnoœci te, których opóŸnienie wp³ywa w krytyczny sposób na parametry uk³adu. 

### Symulacja modelu dopasowanego i zrealzowanego projektu
Dokonanie symulacji bez syntezy uk³adu umo¿liwia dokonanie wstêpnej obserwacji sygna³ów. Jednak¿e dopiero przesymulowania uk³adu po syntezie i rozmieszczeniu w strukturze FPGA oddaje pe³ny obraz zachowania rzeczywistego projektu. Dziêki niej mo¿emy przeprowadziæ nie tylko analizê funkcjonaln¹, lecz tak¿e sprawdziæ parametry czasowe, opóŸnienia propagacji sygna³ów zegarowych i miêdzyrejestrowych. 

### 3.6.5. Zaprogramowanie uk³adu
Finalny etapem realizacji projektu jest zaprogramowanie uk³adu. Dokonuje siê go przy pomocy zewnêtrznego urz¹dzanie jakim jest programator wykorzystuj¹cy najczêœciej standard JTAG.

# 4. System sterowania nadajnikami
## 4.1. Za³o¿enia

## Usprawnienia dotychczasowego systemu??

Najwa¿niejszym celem pracy in¿ynierskiej jest usprawnienie i rozszerzenie funkcjonalnoœci omówionego wczeœniej systemu, który mimo i¿ dzia³a³ bardzo dobrze, nie by³ pozbawiony wad. G³ównym problemem, który pojawia³ siê w trakcie eksploatacji, by³ brak mo¿liwoœci szybkiej zmiany parametrów systemu. Ka¿dy z nadajników posiada³ zintegrowany uk³ad CPLD, w którego pamiêci zapisane zosta³y prametry konfiguracyjne. Rozwi¹zanie to jest bardzo wygodne z punktu widzenia konstruktora - tworzymy kilka takich samych uk³adów, które ró¿ni¹ siê tylko bitami zapisanymi w pamiêci. Jednak¿e drobna zmiana parametrów wymaga programowania ka¿dego z uk³adów oddzielnie. Dodatkowo, poniewa¿ gniazdo JTAG zosta³o dodatkowo umieszczone w trudno dostêpnym miejscu - nie jest to proces ³atwy. Ponadto dla ka¿dej z konfiguracji CPLD nale¿y przeprowadziæ syntezê uk³adu, co powodowa³o du¿e nak³ady czasowe. Taki proces uniemo¿liwia³ wrêcz przeprowadzanie wydajnych eksperymentów ze wzglêdu na:

* czas dokonywanych zmian,
* problemy z programowaniem ka¿degu uk³adu z osobna.

Istotnym problemem by³a tak¿e niedoskona³a sekwencja bitów przesy³ana w ³¹czu radiowym. Bitów steruj¹cych by³o zbyt ma³o, a preambu³a ka¿dego z pakietów nie spe³nia³a do koñca swojej roli. Przetwornik A/C umieszczony w pêtli ARW wymaga d³u¿szej sekwencji taktowanej wy¿szym zegarem. Powiêkszenie liczby bitów poprawia tak¿e precyzjê dekodowania sekwencji w odbiorniku.

`odniesienie do opisu we wstêpie na temat roli preambu³y i przetwornika a/c`

W zwi¹zku z tymi problemami zdecydowano siê wprowadziæ udoskonalenia, które zlikwiduj¹ wy¿ej wymienione b³êdy przy jednoczesnym zachowaniu wszystkich funkcji uk³adu

Jednym z mo¿liwych rozwi¹zañ jest wprowadzenie centralnego uk³adu steruj¹cego  który zapewni:

* sterowanie sekwencyjnym uruchamianiem nadajników UWB,
* mo¿liwoœæ ustawienia parametrów konfiguracyjnych uk³adu w jednym miejscu,
* ³atw¹ rozbudowê i skalowalnoœæ,

W omawianej koncepcji rolê centralnego sterownika pe³ni uk³ad FPGA wraz z odpowiedni¹ konfiguracj¹ oraz uk³adami wejœcia-wyjœcia, które zostan¹ przedstawione w kolejnych rozdzia³ach. 

## 4.2. Architektura systemu
Modyfikacja systemu wymaga³a opracowania nowej architektury, która wyeliminuje problemy powsta³e w poprzedniej realizacji. Zdecydowano o zmianie po³¹czenia pierœcieniowego nadajników na rzecz po³¹czenia w gwiazdê wraz z centralnym uk³adem steruj¹cym.

Takie po³¹cznie posiada zdecydowanie wiêcej zalet, kosztem niewielkiej komplikacji uk³adu. Do ka¿dego z nadajników mo¿na wysy³aæ niezale¿nie i sekwencyjnie (b¹dŸ równolegle) sygna³y, których parametry ustawia siê w sterowniku. Ka¿dy z modu³ów radiowych otrzymuje sygna³ zegarowy bezpoœrednio ze sterownika, dziêki czemu system jest niezale¿ny od jitteru wprowadzanego przez ka¿de z urz¹dzeñ (jitter nie kumuluje siê, tak jak w poprzedniej wersji).

`img:archSystemu`
`dok³adniejszy opis`

Pogl¹dow¹ architekturê systemu zaprezentowano na rysunku `img:archSystemu`. Uk³ad FPGA pe³ni g³ówn¹ funkcjê steruj¹c¹. Operator systemu `mo¿e ustawiaæ parametry` oraz wyzwoliæ dzia³anie systemu. Sterownik generuje odpowiednie sygna³y `(zgodnie z ustawieniami)` wysy³aj¹c je na wyjœcia, po czym nastêpuje konwersja standardu przesy³ania danych do potrzeb linii transmisyjnych oraz odbiorników. Z konwertera sygna³y przesy³ane s¹ kablami w standardzie Cat 5e (skrêtka - 4 pary symetryczne) do rozdzielaczy, gdzie s¹ przekazywane do odpowiednich nadajników.

## 4.3. Modu³ FPGA
`zdjêcie p³ytki FPGA`
`schemat`
`krótki opis`

## 4.4. Modu³ konwertera CMOS - LVDS
Uk³ad FPGA Spartan3 firmy Xilinx posiada wyjœcia w ró¿nych standardach. Najbardziej uniwersalnym jest CMOS, w którym:

* stan wysoki => 3,3V b
* stan niski => 0V

Taki sposób kodowania stanów logicznych jest bardzo dobry dla uk³adów pracuj¹cych blisko siebie z krótkimi po³¹czeniami. Jednak¿e przy przesy³aniu sygna³ów d³ugimi kablami nie zdaje on egzaminu, gdy¿ jest bardzo wra¿liwy na zak³ócenia elektromagnetyczne. Ponadto wyjœcia uk³adu nie s¹ dopasowane do obci¹¿enia impedancj¹ linii transmisyjnej.

W zwi¹zku z tym zdecydowano, i¿ do transmisji sygna³ów steruj¹cych zostanie wykorzystany ró¿nicowy standard przesy³ania danych LVDS, opisany w `dodatku 9.1`. Mimo i¿ sam uk³ad FGPA Spartan3 posiada wyjœcia w tym standardzie, to nie mo¿na ich wykorzystaæ ze wzglêdu na brak kompensacji d³ugoœci wszystkich œcie¿ek na p³ytce. Konwerter sygna³ów zosta³ zrealizowany jako modu³ na oddzielnej p³ytce drukowanej ze z³¹czem umo¿liwiaj¹cym ³atwe do³¹czenie do bazowego systemu z uk³adem FPGA.

`img:pcbSchemat`

Do konwersji wykorzystano uk³ady MAX9157 firmy Maxim, które (na podstawie `bibl:datasheetMAX9517`):

* obs³uguj¹ cztery kana³y transmisji CMOS -> LVDS lub LVDS -> CMOS,
* umo¿liwiaj¹ transmisjê strumieni o przep³ywnoœci do 200Mbps,
* odbieraj¹ sygna³y ró¿nicowe o poziomach ju¿ od 100mV,
* posiadaj¹ obwody zabezpieczaj¹ce wyjœcie przed niepo¿¹danym stanem na wejœciu (fail-save input receiver),
* umo¿liwiaj¹ pod³¹czania i od³¹czanie w trakcie pracy uk³adu (hot-swappable).

Mo¿liwoœci te sprawiaj¹, ¿e uk³adu MAX9157 s¹ bardzo dobrymi elementami do budowy interfejsów do przesy³ania danych d³ugimi kablami.

![Schemat zasilania](./img/zasilanie.png "img:zasilanie")

Ze wzglêdu na du¿y pobór pr¹du przez nadajniki ca³y system nie mo¿e zostaæ zasilony przez p³ytkê z modu³em FPGA. Zdecydowano o zastosowaniu dodatkowego zasilacza, który dostarczy odpowiedniej mocy do konwertera oraz nadajników (co zosta³o zobrazowane na rysunku `img:zasilanie`). Do wolnej pary (do transmisji danych wykorzystano tylko 3 z 4 par) pod³¹czone zostanie napiêcie zasilania oraz masa. Potencja³y te s¹ pod³¹czone z obu rozdzielaczy jednoczeœnie i s¹ po³¹czone poprzez diody oraz filtry z³o¿one z kondensatora i d³awika, którego celem jest odfiltrowanie wszelkich zak³óceñ oraz separacja potencja³ów analogowych i cyfrowych (aVcc, aGnd, Vcc, cGnd).

`img:pcbLayout`

Zaprezentowany na rysunku `img:pcbLayout` layout p³ytki zosta³ stworzony w programie Altium Designer 6. Rozmieszczenie wyprowadzeñ w uk³adach MAX9157 jest bardzo przyjazne dla konstruktura i u³atwia prowadzenie œcie¿ek (wejœcia po jednej stronie, wyjœcia po drugiej, przeciêcie p³aszyczyny masy idealnie w po³owie uk³adu). Mimo to nie oby³o siê bez problemów z poprowadzeniem zasilania, co wymusi³o dolutowanie zwor do p³ytki.

`img:pcbPhoto`

Uruchamianie uk³adu konwertera przebieg³o bez wiêkszych problemów. Pierwszym krokiem by³o sprawdzenie doprowadzeñ zasilania poprzez pod³¹czenie napiêcia sta³ego do œcie¿ek rozprowadzaj¹cych je po uk³adzie. Napiêcie na wyjœciu stabilizatora wynios³o 3.3V. Nastêpnie pod³¹czono konwerter do modu³u z FPGA oraz rozdzielacze do wyjœcia. Na oscyloskopie zaobserwowano przebiegi sygna³ów ró¿nicowych, jednak¿e ze wzglêdu na rozwarcie na koñcu linii by³y one zniekszta³cone. Dopiero pod³¹czenie dopasowanych generatorów umo¿liwi³o obserwacjê poprawnych sygna³ów.


## 4.5. Struktura generowanych sygna³ów ##

### 4.5.1. Struktura pakietu ###
System lokalizacyjny, do realizacji swoich funkcji, wykorzystuje sekwencje sygna³ów przesy³anych w ³¹czu radiowym. Nadajniki przesy³aj¹ zestandaryzowane sekwencje bitów, których ka¿de pole sk³adowe reprezentuje wykonanie odpowiednich procedur w odbiorniku. Po detekcji przesy³anej sekwencji odbiornik realizuje funkcjê okreœlon¹ przez ci¹g bitów. Struktura logiczna przesy³anych danych zosta³a zaprezentowana na rysunku `img:SchPak1`.

![Struktura pakietu](./img/pakiet.png "img:SchPak1")

W schemacie pakietu informacyjnego mo¿emy wyró¿niæ kilka pól, które uruchamiaj¹ odpowiednie funkcje odbiornika. S¹ to:
* PRMB
* STPS
* BSTP
* IDN
* STRS
* BSTR

Ka¿dy z nich odpowiada za inicjalizacjê odpowiedniego procesu w odbiorniku, które po zakoñczeniu umo¿liwiaj¹ okreœlenie ró¿nicy czasów propagacji sygna³ów i finalnie obliczenie pozycji. 

1. **PRMB** - preambu³a. Sk³ada siê z ok. 20 impulsów. Nie niesie treœci informacyjnej, jednak¿e jest bardzo istotna z energetycznego punktu widzenia. Umo¿liwia bowiem uk³adom odbiornika okreœlenie poziomu sygna³u, z jakimœ bêd¹ transmitowane kolejne bity. Wejœciowy uk³ad *ARW* (ARW - Automatyczna Regulacja Wzmocnienia) dostosowuje parametry wzmacniacza wejœciowego do poziomu mocy odebranej preambu³y. Po ustaleniu tych parametrów odbiornik jest gotowy do odebrania i detekcji kolejnych bitów, które ju¿ nios¹ konkretn¹ treœæ informacyjn¹.
1. **STPS** - odblokowanie zatrzymania pomiaru czasu.
1. **BSTP** - zatrzymanie pomiaru czasu.
1. **IDN** - identyfikator nadajnika. D³ugoœæ tego pola (32 bity) wynika ze sposobu realizacji pomiaru przez uk³ady odbiornika. Wykorzystany do pomiaru uk³ad TDC (*Time to Digital Converter*) typu GP2 produkcji firmy Acam wymaga odpowiedniego czasu, aby wystawiæ na swoje wyjœcia wynik pomiaru oraz przygotowaæ siê do realiazacji kolejnego pomiaru.
1. **STRS** - odblokowanie uruchomienia pomiaru czasu.
1. **BSTR** - uruchomienie pomiaru czasu.

Krótkiego wyjaœnienia wymaga kolejnoœæ transmitowanych pakietów - najpierw pomiar jest zatrzymywany, a póŸniej dopiero uruchamiany. Jest to konsekwencja zastosowanego systemu TDOA, gdzie mierzone s¹ ró¿nice czasów dotarcia sygna³ów od poszczególnych nadajników. 

`szczegó³owy opis - rozdzia³ o TDOA`

### 4.5.2. Parametry czasowe ###

System transmisyjny oraz charakterystyka kana³u radiowego narzucaj¹ okreœlone wymagania co do parametrów parametrów czasowych przesy³anych sekwencji.

![OdpowiedŸ impulsowa kana³u radiowego - przyk³ad](./img/impulseResponse.gif "img:kanalRadiowy")

Na rysunku `img:kanalRadiowy - rysunek pogl¹dowy œci¹gniêty z internetu` przedstawiono przyk³adow¹ charakterystykê odpowiedzi impulsowej kana³u radiowego po pobudzeniu impulsem UWB. Mo¿na zauwa¿yæ kilka charakterystycznych fragmentów. Pierwszy, wyraŸny pik jest sygna³em, który dotar³ bezpoœrednio od nadajnika do odbiornika. Po krótkiej przerwie pojawiaj¹ siê kolejne fragmenty sygna³u, które powsta³y poprzez niekorzystne zjawisko propagacji wielodrogowej (sygna³ nadany odbija siê od du¿ych (w stosunku do d³ugoœci fali) obiektów i dociera do odbiornika z opóŸnieniem). Te sk³adowe mog¹ zaburzyæ poprawnoœæ odbioru, gdy¿ urz¹dzenie odbiorcze nie jest w stanie rozró¿niæ impulsów bezpoœrednich od odbitych. 

W zwi¹zku z powy¿szym faktem na etapie projektowania sygna³ów transmitowanych drog¹ radiow¹ nale¿y zwróciæ szczególn¹ uwagê na odstêp miedzybitowy. Odpowiedni jego dobór jest kompromisem pomiêdzy czasem dzia³ania systemu (krótki odstêp), a uchronieniem siê od sk³adowych wielodrogowych (wiêkszy odstêp). W trakcie badañ poprzedzaj¹cych projektowanie systemu stwierdzono, i¿ dla zak³adanych warunków pracy odstêp miêdzybitowy na poziomie *200-300 \[ns\]* jest ca³kowicie wystarczaj¹cy i skutecznie wyeliminuje omawiany problem.

Z okreœlonego odstêpu miêdzybitowego wynika wprost czêstotliwoœæ z jak¹ nale¿y generowaæ impulsy. Zawiera siê ona w przedziale od 3.33  do 5 MHz. Powy¿szym rozwa¿aniom nie podlega jednak sygna³ preambu³y, w którym okres powtarzania impulsów wynosi *20 \[ns\]*, wobec czego czêstotliwoœæ taktowania uk³adów generowania preambu³y wynosi 50 \[MHz\].

### 4.5.3. Modulacja ###

Do przesy³ania danych w ³¹czu radiowych czêsto wykorzystuje siê modulacjê *OOK* (OOK - On-Off Keying), której ideê prezentuj¹ rysunki `img:OOK1` oraz `img:OOK2`

![Sygna³ oryginalny - Ÿród³o: National Instruments (www)](./img/OOK_1.gif "img:OOK1")

![Sygna³ zmodulowany - Ÿród³o: National Instruments (www)](./img/OOK_2.gif "img:OOK2")

Logicznej jedynce odpowiada wys³anie noœnej (lub, tak jak w omawianym przypadku, impulsu UWB). Brak sygna³u to logiczne zero.

W omawianym systemie zastosowano zmodyfikowan¹ wersjê tej modulacji. W ³¹czu radiowym transmitowane s¹ sygna³u UWB, w zwi¹zku z czym logicznej jedynce odpowiada generacja impulsu; natomiast logiczne zero to brak nadawania. Zastosowane generatory UWB s¹ wyzwalane narastaj¹cym zboczem sygna³u wejœciowego. W zwi¹zku z tym, nale¿y im dostarczyæ przebieg wejœciowy, który zmieni swój stan z 0 na 1 w momencie po¿¹danej generacji. Ma to istotne znaczenie z punktu widzenia kszta³towania sygna³ów w uk³adzie FPGA.

# 5. Konfiguracja FPGA 
## 5.1. Wprowadzenie
Opisane w rozdziale `Programowalne uk³ady cyfrowe` struktury FPGA s¹ bardzo wygodnym narzêdziem do budowania elektronicznych systemów cyfrowych. Dziêki mo¿liwoœci zaimplementowania wielu klasycznych elementów (liczniki, rejestry, automaty stanów) i szerokiej ich rozbudowy mo¿na zaprojektowaæ nawet bardzo z³o¿one uk³ady. Podzia³ na struktury hierarchiczne u³atwia zarówno budowanie uk³adu jak i jego póŸniejsz¹ analizê.

## 5.2. Interfejs zewnêtrzny i opcje konfiguracyjne
`opisanie sterowania uk³adem, brak implementacji póki co`
`jakie stany (elektryczne i logiczne) co wyzwalaj¹`
`poziomy napiêæ?`

Sygna³y wejœciowe | Opis |
-----------------|------|
`clk_in` |  wejœcie sygna³u zegarowego wraz z buforem zapewniaj¹cym optymaln¹ propagacjê sygna³u w uk³adzie |
`start` | uruchomienie uk³adu |
`rst` | reset asynchroniczny |

Sygna³y wyjœciowe | Opis |
------------------|------|
`wyjœcia` | szeœæ wyjœæ wygenerowanych sygna³ów 

## 5.3. Top module
Na najwy¿szym stopniu hierarchii projektu znajduje siê element `top module`. W uk³adzie zdefiniowano wszystkie wymienione wczeœniej wejœcia, wyjscia oraz po³¹czenia miêdzy poszczególnymi blokami sk³adowymi. Na rysunku `img:topModule` mo¿emy wyró¿niæ
* `automat` - który steruje dzia³aniem pozosta³ych bloków,
* `trx1..6` - zestaw bloków generuj¹cych sygna³y steruj¹ce poszczególnymi nadajnikami,k
* `dzielniki czêstotliwoœci` - bloki umo¿liwiaj¹ce dostosowanie czêstotliwoœci sygna³u zegarowego do potrzeb ró¿nych bloków funkcjonalnych

### 5.3.1. Automat steruj¹cy

![Automat steruj¹cy](./img/blok_main_automat.png "img:blokMainAutomat")

Bloki generuj¹ce sygna³y s¹ sterowane przez automat zarz¹dzaj¹cy, który:

* czeka na polecenie u¿ytkownika do rozpoczêcia generacji,
* uruchamia pierwszy generator,
* czeka na informacjê zwrotn¹, po otrzymaniu której uruchamia kolejny generator
* analogicznie uruchamia kolejne generatory
* `umo¿liwia generacjê pojedyncz¹ lub ci¹g³¹`
* `umo¿liwia sterowanie odstêpem miêdzybitowym`

![Automat steruj¹cy](./img/diagram_abstract.png "img:abstractDiagram")

![Automat steruj¹cy](./img/diagram_closer.png "img:closerDiagram")

Na pierwszym z powy¿szych rysunków zaprezentowano diagram stanów automatu steruj¹cego, gdzie ka¿dy proces generacji opisano pojedynczym stanem. Drugi z rysunków pokazuje fragment pierwszego z uwzglêdnieniem konkretnych stanów rzeczywistego automatu. Jest to automat typu Mealy'ego, gdy¿ wyjœcia uk³adu zale¿ne s¹ nie tylko od aktualnego stanu, ale tak¿e od wartoœci logicznej sygna³ów wejœciowych. 

### 5.3.2. Dzielniki czêstotliwoœci

![Dzielniki czêstotliwoœci](./img/blok_clk_div.png "img:dzieniki")

Ze wzglêdu na ró¿ne czasy trwania generowanych w uk³adzie nale¿a³o wytworzyæ sygna³y zegarowe o ró¿nej czêstotliwoœci, przy czym nale¿y pamiêtaæ o zapewnieniu synchronizmu miêdzy nimi. Aby to osi¹gn¹æ wykorzystano elementy, które podziel¹ czêstotliwoœæ o odpowiedni¹ wartoœæ, co skutkuje wyd³u¿eniem czasu trwania okresu zegara. 

Proste dzielniki mog¹ byæ wykonane jako z³o¿enie kilku przerzutników. W prostym przypadku dzielenia przez 2 implementacja takiego bloku funkcjonalnego sk³ada siê z jednego przerzutnika D oraz negatora wpiêtego w pêtlê sprzê¿enia zwrotnego do wejœcia D.

![Dzielnik przez 2](./img/blok_clk_div2.png "img:dzienik2")

W bardziej z³o¿onych przypadkach warto pos³u¿yæ siê jêzykiem VHDL, w którym mo¿na zaimplementowaæ taki blok, którego wspó³czynnik podzia³u bêdzie dowolnie definiowalnym parametrem.

`process (clk_in) begin
	if (clk_in'event and clk_in = '1') then
		if cnt >= DIV_FACTOR then
			div_temp <= not(div_temp);
			cnt <= 0;
		else	
			div_temp <= div_temp;
			cnt <= cnt + 1;
		end if;
		div_10 <= div_temp;
	end if;
	end process;`

## 5.4. "Single TRX Generator"
Na najwy¿szym stopniu hierarchii umieszczonych zosta³o 6 uk³adów generuj¹cych sygna³y wyzwalaj¹ce poszczególne nadajniki. Uk³ady te reprezentuje makroblok o strukturze przedstawionej na rysunku `:img:struktura makrobloku`:

`img:struktura makrobloku`

![Blok automat](./img/blok_automat.png "img:blokAutomat")


Sygna³y wejœciowe | Opis |
-----------------|------|
clk              | g³ówny sygna³ zegarowy synchronizuj¹cy pracê uk³adu (100 \[MHz\]) |
clk preamb       | sygna³ zegarowy taktuj¹cy generowanie preambu³y (`ile?`) |
clk data         | sygna³ zegarowy taktuj¹cy generowanie bitów informacyjnych  (`ile?`) |
start            | wyzwolenie generacji sekwencji bitów |
rst              | reset asynchroniczny |


Sygna³y wyjœciowe | Opis |
-----------------|------|
`out`            | g³ówne wyjœcie generowanej sekwencji |
`finish_preamb`  | sygna³ informuj¹cy o zakoñczeniu generacji preambu³y |
`finish`         | sygna³ informuj¹cy o zakoñczeniu generacji ca³ej sekwencji |

Ka¿dy z nich posiada bliŸniacz¹ wewnêtrzn¹ strukturê, która sk³ada siê z:

* zestawu wejœæ,
* automatu steruj¹cego,
* dwóch liczników,
* uk³adu kombinacyjnego,
* multiplekserów wyjœciowych.

### 5.4.1. Automat steruj¹cy
Prac¹ makrobloku steruje g³ówny automat, który uruchamia sekwencyjnie kolejne bloki zgodnie z diagramem stanów przedstawionym na rysunku `img:diagramStanow`.

![Automat steruj¹cy](./img/automat.png "img:diagramStanow")

Automat, bêd¹c w stanie pocz¹tkowym, czeka na wyzwolenie sygna³em start, który pochodzi z uk³adów na wy¿szym poziomie hierarchii. Gdy sygna³ ten siê pojawi uruchomiona zostaje generacja preambu³y.

Za proces ten odpowiada licznik `cnt_20`, który jest taktowany zegarem 50 \[MHz\], co odpowiada czêstotliwoœci sygna³u preambu³y. Uruchomienie licznika powoduje wys³anie na wyjœcie `preamb` sygna³u o tej w³aœnie czêstotliwoœci. Wyjœciowy multiplekser jest w stanie "0, czyli sygna³ preambu³y pojawia siê na wjœciu `out` makrobloku. 

Po przepe³nieniu licznika `cnt_20` wysy³any jest impuls potwierdzaj¹cy do g³ównego automatu. Zmiana stanu rozpoczyna kolejny proces - generacjê sekwencji informacyjnej - poprzez uruchomienie licznika `cnt_72`, którego stan adresuje uk³ad ROM. OdpowiedŸ `uk³adu pamiêciowego` przechodzi przez multipleksery wyjœciowe (opisane w rozdziale 5.4.3), a nastêpnie sekwencja jest wystawiana na wyjœcie ca³ego makrobloku.

### 5.4.2. ROM 

Sekwencje informacyjne, przesy³ane do poszczególnych nadajników, s¹ ró¿ne i musi byæ zapisana w konfiguracji uk³adu. Nale¿a³o zatem wprowadziæ element, który przechowywa³by dane oraz umo¿liwia³ w ³atwy sposób ich ewentualn¹ zmianê.

Rozwa¿ano zastosowanie specyficznych dla uk³adów z rodziny Xilinx Spartan3 rozwi¹zañ, które umo¿liwiaj¹ wygenerowanie w strukturze FPGA pamiêci typu *Read Only Memory*. Jednak¿e, ze wzglêdu na ma³¹ uniwersalnoœæ takiej realizacji, zdecydowane o stworzeniu prostszej i bardziej "przenoœnej" implementacji. Zamiast pamiêci ROM u¿yto klasycznego uk³adu kombinacyjnego w postaci tablicy prawdy. Jej opis w jêzyku VHDL nadaje uniwersalnoœci i pozwala przeprowadziæ syntezê dla dowolnych uk³adów FPGA.

![Blok ROM](./img/blok_rom.png "img:blokRom")

Z punktu widzenia zacisków wejœciowych i wyjœciowych uk³ad zachowuje siê identycznie jak pamiêæ ROM.

#### Generator tablicy prawdy

Przenoœnoœæ powy¿szego rozwi¹zania osi¹gniêta przez realizacjê w jêzyku VHDL poci¹ga za sob¹ ma³¹ czytelnoœæ kodu (dla osoby nieznaj¹cej tej technologii) oraz ¿mudny proces zmiany wartoœci, jeœli zajdzie taka koniecznoœæ. Aby u³atwiæ edycjê parametrów stworzono prosty program w jêzyku Java, który umo¿liwia automatyczne wygnerowanie pliku VHDL opisuj¹cego dan¹ tablicê prawdy.

![Program JAVA - generator VHDL](./img/java_program.png "img:generatorVHDL1")

Po uruchomieniu programu wystarczy uzupe³niæ pola:
* `entity` - nazwa danego bloku,
* wartoœci bitów ka¿dego z bloków,
* nazwa pliku.

Naciœniêcie przycisku `generuj` utworzy w katalogu programu plik opisuj¹cy tablicê prawdy z ustawionymi przez u¿ytkownika parametrami.

![Efekt pracy generatora](./img/java_plik_wygnerowany.png "img:generatorVHDL2")

### 5.4.3. Multipleksery wyjœciowe
Zapewnienie generacji impulsu przy ka¿dym wyst¹pieniu jedynki logicznej wymaga odpowiedniego zakodowania sygna³u na wyjœciu uk³adu FPGA - ka¿dej jedynce musi odpowiadaæ narastaj¹ce zbocze. Zrealizowanie takiego kodowania jest mo¿liwe na kilka sposobów.

W pierwszym podejœciu po³¹czono wyjœcie informacyjne z sygna³em zegarowym o odpowiedniej czêstotliwoœci zwyk³¹ bramk¹ AND. Z punktu widzenia logiki boolowskiej oraz symulacji behawioralnych rozwi¹zanie to jest poprawne. W rzeczywistym uk³adzie jednak powodowa³o to pewne problemy - na wyjœciu bramki pojawia³y siê "szpilki" w trakcie opadaj¹cego zbocza zegarowego, które mog³yby wyzwoliæ generatory UWB.

W zwi¹zku z tym zast¹piono bramkê AND multiplekserem przystosowanym do prze³¹czania sygna³ów zegarowych (specyficznego dla uk³adu Spartan3). 

`rysunek!!!!`


### Realizacja regulacji przesuniêæ

### Testowanie

## Interfejs 

# 6. Badania

## Cel i zakres badañ
Celem badañ jest weryfikacja realizacji projektu pod k¹tem zdefiniowanych wczeœniej wymagañ. Nale¿y sprawdziæ, czy parametry okreœlone we wstêpnych za³o¿eniach spe³niaj¹ okreœlone kryteria. Opisane w `rozdziale 5.5` symulacje potwierdzaj¹ zgodnoœc z za³o¿eniami, jednak¿e pe³n¹ wartoœæ projektu mog¹ oddaæ tylko rzeczywiste pomiary.

## Uk³ad pomiarowy 

Uk³ad pomiarowy sk³ada siê z:

* pe³nego systemu sterownika opracowanego w ramach pracy,
* p³ytki konwertera standardu LVDS -> LVPECL,
* oscyloskopu próbkuj¹cego TexasInstruments TDS8200.

`rysunek`

P³ytka konwertera LVDS->LVPECL oparta zosta³a na uk³adach MAX9375. Standard LVPECL (Low Voltage Positive Emmiter-Coupled Logic) umo¿liwia dystrybucjê bardzo szybkich sygna³ów cyfrowych w liniach 50 `omowych`.

## Metodyka pomiarów

Przeprowadzenie dok³adnych badañ parametrów czasowych wymaga synchronizacji wyzowlenia oscyloskopu z badanym sygna³em. Aby zapewniæ spe³nienie tego warunku dokonano niewielkiej modyfikacji uk³adu wyprowadzaj¹c jeden z wewnêtrznych sygna³ów do wyjœcia uk³adu FGPA. Sygna³ ten jest zsynchronizowany z pocz¹tkiem cyklu generacji pakietów, w zwi¹zku z czym mo¿e zostaæ u¿yty do wyzwolenia oscyloskopu.

`rysunek - paczka i wyzwolenie`

Po zsynchronizowaniu oscyloskopu realizowano pomiary poprzez standardowe funkcje dostêpne w cyfrowych urz¹dzeniach pomiarowych, takie jak *marker*, *delta marker*, *burst width measure* itd.

## Pomiar parametrów czasowych sygna³ów

### Szerokoœæ paczki (burst width)

### Szerokoœæ preambu³y 

### Szerokoœæ impulsu

### Odstêp miêdzybitowy

## Pomiar parametru jitter

W systemach okreœlaj¹cych bardzo dok³adnie pozycjê istotnym parametrem jest jitter. Niewielkie wahania momentu wyzwolenia sygna³u mo¿e powodowaæ du¿y b³¹d dok³adnoœci okreœlenia pozycji (`opisane w rozdziale o lokalizacji uwb`). St¹d wynika rygorystyczne wymaganie na ten parametr.

`metodyka badania jittera`

Na pocz¹tku zbadano jitter samego zegara umieszczonego na p³ytce z modu³em FPGA, którego du¿a wartoœæ stawia³aby pod znakiem zapytania sens stosowania takiego modu³u w sterowniku. Zbadano sygna³, którym taktowane jest generowanie sekwencji danych (tj. zegar g³ówny po podzieleniu przez 10) i otrzymano wartoœæ 10 [ps], co mo¿na uznaæ za bardzo dobr¹. Kolejne modu³y bêd¹ do tej wartoœci dodawaæ swój jitter.

`jaki jitter ma max9157 i max9375 (2ps RMS)`

# 7. Podsumowanie

# 8. Bibliografia
* `bib:LVDS` Low-Voltage Differential Signaling, International Engineering Consortium, 
* `bibl:praca p.Kosiñskiego` - praca magisterska 
* `bibl:datasheetMAX9517`
* `bibl:VHDL` Jêzyk VHDL - Kevin Skahill
* `bibl:spartan` Xilinx Spartan 3 FPGA Datasheet

# 9. Dodatki
## 9.1. Standard LVDS

Do transmisji danych w kablach doprowadzaj¹cych sygna³y do generatorów stosowany jest standard LVDS `(rys. img:LVDS)`. Jest to ró¿nicowy sposób transmisji danych, gwarantuj¹cy:

* wysok¹ energooszczêdnoœæ,
* wysok¹ przep³ywnoœæ,
* ochronê przed zak³óceniami elektromagentycznymi.

![Standard LVDS - Ÿród³o: National Instruments (www)](./img/lvds.png "img:LVDS")

`bib:LVDS` Ró¿nicowy standard transmisji polega na wykorzystaniu dwóch skrêconych ¿y³ jako linii sygna³owych (o dwóch ró¿nych polaryzacjach) zamiast po jednej sygna³owej i masy. Nadajnik wymusza przep³yw pr¹du o ma³ym natê¿eniu (zazwyczaj *i = 3.5 \[mA\]*), który w odbiorniku przep³ywa przez rezystor dopasowuj¹cy wejœcie do linii transmisyjnej (zazwyczaj *R = 100 - 150 \[ohm\]*). Pierwszym stopniem odbiornika jest wzmacniacz o wejœciu ró¿nicowym o du¿ym wzmocnieniu sk³adowej ró¿nicowej, co zapewnia poprawny odbiór niewielkich sygna³ów. Ponadto takie uk³ady posiadaj¹ du¿e t³umienie sk³adowej wspólnej (sumacyjnej), co sprawia, ¿e wystêpuj¹ce w obu liniach sygna³owych jednoczeœnie zak³ócenia elektromagnetyczne, nie maj¹ wp³ywu na poprawnoœæ odebranego sygna³u.




