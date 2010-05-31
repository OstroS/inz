* Table of contents
{:toc}

___
# 1. Wst�p  

# 2. Systemy lokalizacyjne UWB

## 2.1. Sygna�y UWB 

### 2.1.1. Charakterystyka
UWB (Ultra Wide Band) to technologia umo�liwiaj�ca przesy�anie sygna��w radiowych o bardzo du�ej szeroko�ci pasma. Wed�ug norm FCC (Federal Communications Commission) sygna� ultraszerokopasmowy posiada wzgl�dn� szeroko�� pasma (okre�lon� jako pasmo 10dB spadku od poziomu sk�adowej o cz�stotliwo�ci �rodkowej) wi�ksz� od 20% lub bezwzgl�dn� szeroko�� pasma wi�ksz� od 500MHz. W Europie, gdzie organem reguluj�cym jest Komisja Europejska, sygna�em ultraszerokopasmowym nazywamy taki, kt�rego bezwgl�dna szeroko�� pasma jest wi�ksza ju� od 50MHz.

Zgodnie z twierdzeniem Shannona maksymalna mo�liwa do osi�gni�cia przep�ywno�� transmisji informacji jest wprost proporcjonalna do bezwzgl�dnej szeroko�ci pasma sygna�u. W zwi�zku z tym sygna�y UWB maj� potencjalnie bardzo du�e mo�liwo�ci z punktu widzenia przesy�ania strumieni danych o du�ej przep�ywno�ci. Dodaktowo szerokie pasmo umo�liwia ograniczenie mocy nadawanego sygna�u, dzi�ki czemu urz�dzania wykorzystuj�ce UWB do transmisji radiowej b�d� bardziej energooszcz�dne. Dzi�ki impulsowej pracy i niewielkim mocom sygna��w systemy te mog� pracowa� w zaj�tych ju� pasmach b�d�c praktycznie niewykrywalne przez osoby postronne.

Transmisja radiowa wykorzystuj�ca UWB ma przed sob� ciekaw� przysz�o��. Dzisiejsze mobilne systemy s� coraz bardziej miniaturyzowane i narzucane s� na nie wysokie wymagania dotycz�ce zu�ycia energii. Ponadto urz�dzania staj� si� coraz bardziej multimedialne, w zwi�zku z czym rosn� oczekiwania co do obs�ugiwanych przep�ywno�ci strumieni danych. Wprowadzenie system�w UWB do transmisji danych na pewno u�atwi producentom sprz�tu spe�nienie rosn�cych wymaga�.

### 2.1.2. Propagacja

## 2.2. Systemy TDOA
Systemy lokalizacyjne jeszcze do niedawna kojarzy�y si� g��wnie z lotniczymi i wojskowymi radarami. W dzisiejszych czasach lokalizacja urz�dze� coraz �mielej wkracza w r�ne dziedziny �ycia bliskie ka�emu cz�owiekowi. Dobrym tego przyk�adem tego zjawiska jest telefonia kom�rkowa, kt�rej operatorzy s� zobligowani do wprowadzenia technicznych rozwi�za� umo�liwiaj�cych odpowiednim s�u�bom lokalizacj� terminala. Pojawiaj� si� tak�e systemy, kt�rych celem jest okre�lenie dok�adnej pozycji i przemieszczenia danego czujnika wewn�trz budynku lub pojedynczego pomieszczenia.
Opracowano wiele technik i modeli matematycznych umo�liwiaj�cych okre�lenie pozycji w r�nych warunkach. Do najbardziej popularnych metod nale��:

* RSS (Recieved Signal Strenght) - oparta na pomiarze poziomu mocu sygna�u,
* AOA (Angle of Arrival) - oparata na pomiarze k�ta nadej�cia sygna�u,
* TOA (Time of Arrival) - oparta na pomiarze czasu propagacji sygna��w w ��czu radiowym
* TDOA (Time Difference of Arrival) - oparta na pomiarze r�nicy czas�w propoagacji sygna��w w ��czu radiowym.

Z punktu widzenia omawianej pracy najistotniejsze jest om�wienie ostatniej z wymienionych metod, czyli TDOA. Opiera si� ona na wyznaczeniu odst�p�w czasowych pomi�dzy sygna�ami docieraj�cymi z r�nych w�z��w sieci. Na podstawie tych parametr�w mo�na obliczy� po�o�enie, kt�re wypada na przeci�ciu odpowiednik hiberboli (w przestrzeni dwuwymiarowej) lub hiberboloid (w przestrzeni tr�jwymiarowej).

`rysunek`

Niew�tpliw� zalet� systemu TDOA jest brak konieczno�ci synchronizacji zegar�w odbiornika z w�z�ami referencyjnymi, gdy� istotne s� tylko r�nice w czasie docieraj�cych sygna��w. Nie ma zatem konieczno�ci stosowania bardziej wyrafinowanych metod umo�liwiaj�cych dok�adn� synchronizacj�. 

Istniej� dwa warianty omawianej metody. W pierwszej z nich sygna�y nadawane s� od w�z��w referencyjnych w stron� obiektu lokalizowanego, kt�ry jest odbiornikiem. Umo�liwia to lokalizowanie jednoczesne wielu urz�dze� b�d�cych w oszarze dzia�ania systemu, jednak�e komplikuje to budow� odbiornika, w kt�rym nale�y zaimplementowa� algorytmy obliczaj�ce pozycj�. W drugiej wersji to lokalizowane urz�dzenie jest nadajnikiem, a w�z�y referencyjne odbieraj� sygna�. Zalet� tego rozwi�zania jest uproszczenie urz�dzenia lokalizowanego i przeniesienie bloku obliczaj�cego pozycj� do jednego z w�z��w. Taki system wymaga jednak wprowadzenia mechanizmu wielodost�pu, aby m�c lokalizowa� kilka urz�dze� na raz. 

`Kr�tkie impulsy umo�liwiaj� precyzyjne okre�lenie po�o�enia`

## 2.3. System opracowany w PMR przez mgr Kosi�skiego (tytu� roboczy)

### 2.3.1. Architektura

Opracowany i opisany w `bibl:praca p.Kosi�skiego` system sk�ada si� z z pi�ciu nadajnik�w (uk�ad cyfrowy CPLD, generator UWB oraz antena) po��czonych szeregowo (struktura zosta�a przedstawiona na `rys 2.1`). Pierwszy z nich jest nadajnikiem nadrz�dnym, kt�ry:

* decyduje o rozpocz�ciu procesu generacji i wysy�aniu impuls�w w ��czu radiowym,
* uruchamia kolejny nadajnik,
* jest �r�d�em sygna�u zegarowego.

Ka�dy z kolejnych nadajnik�w otrzymuje sygna� zegara oraz sygna� wyzwalaj�cy. Zegar jest regenerowany i wysy�any dalej, po czym jest u�ywany jako lokalny sygna� zegarowy, dzi�ki czemu wszystkie nadajniki s� ze sob� zsynchronizowane. Po otrzymaniu sekwencji steruj�cej, ka�dy nadajnik wysy�a impulsy w ��czu radiowym, kt�re steruj� prac� odbiornika. Odpowiednie sekwencje uruchamiaj� i zatrzymuj� pomiar czasu, a tak�e nios� tre�� informacyjn� umo�liwiaj�c� zidentyfikowanie konretnego nadajnika. Odbiornik, zgodnie ze sposobem dzia�ania system�w typu TDOA, mierzy r�nic� czas�w pomi�dzy otrzymaniem sygna��w z poszczeg�lnych nadajnik�w. Po wys�aniu sekwencji z ostatniego nadajnika pomiar si� ko�czy i odbiornik przechodzi do obliczania pozycji korzystaj�c z zaprogramowanych algorytm�w.

![Schemat uk�adu ](./img/kosinski.png "img:Rys2.1")

### 2.3.2. Sygna�y w ��czu radiowym

W ��czu radiowym systemu nadawane by�y pakiety o strukturze przedstawionej na rysunku `rys 2.2`.

![Uproszczony schemat sygna��w w ��czu radiowym ](./img/kosinski_sygnaly.png "Rys2.2")

Preambu�a umo�liwia wysterowanie uk�adu automatycznej regulacji wzmocnienia. Nast�pnie przesy�ana jest komenda STOP, kt�ra zatrzymuje pomiar czasu. Bity identyfikatora umo�liwiaj� odbiornikowi rozpoznanie �r�d�a przesy�anego sygna�u. Pakiet ko�czy komenda uruchomiaj�ca pomiar.

# 3. Systemy Cyfrowe

## 3.1. Klasyczne Systemy Cyfrowe
Koniec ubieg�ego wieku przyni�s� niesamowity rozw�j system�w elektronicznych. Odst�piono od elektroniki analogowej i zacz�to projektowa� oraz produkowa� na masow� skal� uk�ady cyfrowe. W fazie projektowania wykorzystywano mechanizmy oparte na algebrze Boola - tworzono opis uk�adu w postaci tablicy prawdy, kt�r� za pomoc� r�norodnych technik optymalizacyjnych (tablice Karnough'a, dekompozycja) sprowadzano do postaci r�wnania boolowskiego. Nast�pnie tworzono realizacj� r�wna� przy pomocy bramek logicznych, przerzutnik�w, licznik�w, rejestr�w, uk�ad�w arytmetycznych itd. Fizyczn� posta� tworzono najcz�ciej wykorzystuj�c uk�ad�w scalonych firmy Texas Instruments z serii TTL 74xx, kt�re dostarcza�y gotowe implementacje wi�kszo�ci podstawowych struktur logicznych. W trakcie budowania systemu w rol� konstruktora by�o odpowiednie poprowadzenie �cie�ek mi�dzy wej�ciami i wyj�ciami uk�ad�w.

![Fazy projektowania (�r�d�o bibl:VHDL ](./img/fazy_projektowania.png "img:Rys3.1")

Rozw�j system�w poci�gn�� za sob� znaczne skomplikowanie uk�ad�w cyfrowych, co spowodowa�o �e dotychczasowe metody przesta�y by� wystarczaj�ce. D�ugi czas projektowania i z�o�one prototypowanie uniemo�liwa�o szybkie tworzenie nowego sprz�tu. W poszukiwaniu nowych mo�liwo�ci realizacji elektroniki cyfrowej wynaleziono uk�ady programowalne.

## 3.2. Uk�ady logiki programowalnej
Pierwsze uk�ady logiki programowalnej to tzw. uk�ady PAL (*Programmable Array Logic*). Ich wewn�trzna budowa sk�ada�a si� z matrycy bramek AND oraz matrycy bramek OR, gdzie matryca iloczyn�w by�a programowalna, natomiast matryca OR - po��czona na sta�e. 

![Struktura PAL](./img/pal.png "img:Rys3.2")

Dowolne kombinacje po��cze� wewn�trz struktury umo�liwia�y realizacj� bardziej skomplikowanych funkcji w �atwiejszy spos�b. Po raz pierwszy wykorzystano oprogramowanie komputerowe typu CAD (*Computer Aided Design*), kt�re wspomaga�o projektanta w trakcie tworzenia uk�adu. Zmieni�o si� podej�cie do samego procesu projektowania.

![Fazy projektowania (�r�d�o bibl:VHDL) ](./img/fazy_projektowania_cpld.png "img:Rys3.3")

Konstruktor nie musia� samemu realizowa� po��cze� mi�dzy bramkami, gdy� zajmowa�o si� tym oprogramowanie, kt�re dostarcza�o gotow� "map� przepale�" po��cze� wewn�trzych uk�adu PAL.

Wykorzystanie uk�ad�w logiki programowalnej mia�o wiele zalet. Przede wszystkim uwolni�o projektanta od konieczno�ci schodzenia do poziomu bramek logicznych, gdy� zajmowa�o si� tym oprogramowanie. System wymagaj�cy wielu modu��w TTL m�g� sk�ada� si� z jednego uk�adu scalonego realizuj�cego t� sam� funkcj� pracuj�c szybciej. Ograniczono pob�r energii oraz wymagane miejsce na p�ytce. 

Wzgl�dy ekonomiczne r�wnie� przemawia�y za uk�adami PAL. Projekty mog�y by� realizowane i weryfikowane znacznie szybciej, co ogranicza�o koszty. Dzi�ki elastyczno�ci tych modu��w zmiany w dzia�aniu systemu wymaga�y tylko zmiany "mapy przepale�", natomiast sama p�ytka drukowana pozostawa�a bez zmian. Mo�liwe by�o stworzenie uniwersalnych p�ytek ewaluacyjnych umo�liwiaj�cych �atwe prototypowanie uk�adu. 

## 3.3. Uk�ady CPLD	
Kolejnym krokiem w rozwoju programowalnych struktur logicznych by�o pojawienie si� uk�ad�w typu CPLD (*Complex Programmable Logic Device*). Ich struktura sk�ada si� z zestawu blok�w logicznych wraz z cz�ci� odpowiedzialn� za po��czenia wewn�trzne. Ka�dy z blok�w sk�ada si� z:

* matrycy element�w iloczynowych,
* bloku sumy logicznej,
* makrokom�rek.

`schematy, s59`

Blok odpowiedzialny za po��czenia programowalne mo�e by� realizowany na dwa sposoby:

1. po��czenia oparte na matrycy, gdzie wyj�cia ka�dego z blok�w ��czone jest do matrycy poprzez element pami�taj�cy (kom�rka EPROM); ponadto istnieje mo�liwo�� zrealizowania wszystkich po��cze�, tj. dowolne wej�cie mo�e by� po��czone z dowolnym blokiem logicznym.
1. po��czenia oparte na multiplekserze, gdzie ka�demu wej�ciu bloku logicznego odpowiada jeden multiplekser, a linie adresuj�ce s� programowane tak, aby zapewni� odpowiednie po��czenia.

Bloki logiczne swoj� struktur� przypominaj� uk�ady typu PAL.  Bloki te zawieraj� zwykle od 4 do 20 makrokom�rek, przy czym wystarczy ich 16 aby realizowa� szesnastobitowe funkcje logiczne w jednym bloku.

Makrokom�rki sk�adaj� si� z przerzutnik�w oraz uk�ad�w sterowania polaryzacj�, dzi�ki czemu mo�na realizowa� zar�wno funkcje proste jak i zanegowane. Dodatkowo uk�ad CPLD cz�sto posiada makrokom�rki we/wy, kt�re stanowi� bufor i zabezpieczenie w interfejsie I/O.

Uk�ady CPLD posiadaj� r�wnie� inne, ciekawe w�asno�ci. Oferuj� cz�sto konstruktorowi standard ISP (*In System Programmability*), kt�ry umo�liwia programowania uk�adu bezpo�rednio w systemie bez konieczno�ci umieszczania elementu w programatorze. Dodatkowo, nowsze uk�adu implementuj� standard JTAG, kt�ry umo�liwia debuggowanie i testowanie uk�adu pracuj�cego w systemie.

## 3.4. Uk�ady FPGA

**Field Programmable Gate Array** to aktualnie najbardziej rozwini�ty rodzaj programowalnych uk�ad�w logicznych, kt�ry umo�liwia realizacj� bardzo z�o�onych struktur. Posiada mo�liwo�ci identyczne z uk�adami typu ASIC (Application-Specific Integrated Circuit - zintegrowane uk�ady projektowane do zastosowania w konkretnym systemie), dla kt�rych cz�sto stanowi prototyp. Mimo i� uk�ady FPGA s� zazwyczaj wolniejsze i pobieraj� wi�cej mocy mo�na je wykorzystywa� w wielu aplikacjach jako rozwi�zanie ostateczne. Na ich rzecz przemawia kr�tszy czas projektowania oraz ni�sze koszty produkcji.

![Matryca FPGA (�r�d�o bibl:VHDL) ](./img/fpga.png "img:Rys3.5")

Wewn�trzna struktura typowego uk�adu FPGA zosta�a przedstawiona na rysunku 3.3. Mo�emy na niej wyr�ni�:

* bloki wej�cia/wyj�cia,
* bloki logiczne,
* po��czenia programowalne.

Bloki logiczne wraz z programowalnymi po��czeniami stanowi� o ogromnych mo�liwo�ciach uk�ad�w FPGA. Ka�dy z blok�w umo�liwia realizacj� dowolnej funkcji boolowskiej czterech argument�w. Ich wewn�trzna struktura zosta�a przedstawiona na rysunku 3.6 i sk�ada si� z:

![Zarys pojedynczej kom�rki logicznej (�r�d�o bibl:VHDL) ](./img/fpga_LB.png "img:Rys3.6")

* tablicy typu LUT (*Look Up Table*),
* sumatora,
* przerzutnika typu D.

Tablica LUT realizuj� obs�ug� logiki. W jej strukturze zapisana jest tablica prawdy, do kt�rej w trakcie implementacji zosta�o sprowadzone r�wnanie boolowskie lub opis w j�zyki HDL. Przerzutnik umo�liwia synchronizacj� sygna�u wyj�ciowego z dostarczonym sygna�em zegarowym. Za pomoc� multipleksera natomiast mo�na decydowa� czy odpowied� na wyj�ciu ma by� synchroniczna czy asynchroniczna. 

Przy projektowaniu uk�ad�w typu FPGA konstruktor mo�e tworzy� aplikacj� na jeszcze wy�szym poziomie abstrakcji - tj. wy�szym ni� bramki logiczne i r�wnania boolowskie. Wykorzystuje si� w tym celu j�zyki opisu sprz�tu HDL (*Hardware Description Language*, np. *VHDL*, *Verilog*, *AHDL*). Do zaprogramowania konfiguracji FPGA nale�y wykorzysta� �rodowisko dostarczone przez konkretnego dostawc� uk�adu (np. Xilinx - ISE Web Pack, Altera - Quartus). 

### Xilinx Spartan3
Na rynku powszechnie dost�pne s� uk�ady wielu producent�w. Do najbardziej znacz�cych nale�� Altera i Xilinx. Realizacja omawianej pracy zosta�a oparta na uk�adzie Xilinx Spartan3 XC3S200. Posiada on 4 320 kom�rek logicznych, co jest odpowiednikiem ok. 200 000 bramek logicznych. Jego struktura jest rozszerzon� wersj� om�wionej wcze�niej koncepcji i zosta�a przedstawiona na rysunku 3.7.

![Architektura uk�adu FPGA Xilinx Spartn3 XC3S200 (�r�d�o bibl:spartan ](./img/spartan3.png "img:Rys3.7")

Poza podstawowymi elementami, kt�rym s� bloki logiczne, mo�emy wyr�ni� tak�e pami�c typu RAM (sk�adaj�ca si� z blok�w po 18 kilobit�w) oraz blok DCM (Digital Clock Manager), kt�ry dostarcza wszystkich funkcji niezb�dnych z dystrybucj� sygna�u zegarowego oraz operacjach z nim zwi�zanych. Uk�ad posiada 173 linie wej�cia/wyj�cia, kt�re umo�liwiaj� wsp�prac� z sygna�ami przesy�anymi w r�nych standardach zar�wno asymetrycznych (np. LVCMOS) jak i symetrycznych (np. LVDS).

## 3.5. J�zyk VHDL
Tworzenie skomplikowanych system�w cyfrowych wymaga wykorzytania odpowiednich narz�dzi. Opis uk�adu w postaci r�wna� boolowskich jest trudny zar�wno dla projektanta jak i osoby, kt�ra p�niej mo�e system rozwija�. J�zyki opisu sprz�tu umo�liwiaj� stworzenie opisu dzia�ania uk�adu na r�nych poziomach abstrakcji, dzi�ki czemu s� bardziej elastyczne i pozwalaj� szybciej tworzy� skomplikowane struktury. Jednym z dw�ch czo�owych j�zyk�w tego typu, obok j�zyka Verilog, jest VHDL (**V**ery-High-Speed Integrated Circuit **H**ardware **D**escription **L**anguage*), kt�ry zosta� wykorzystany do realizacji projektu w ramach pracy dyplomowej.

J�zyk ten zawiera u�yteczne konstrukcje semantyczne, umo�liwiaj�ce tworzenie jasnego i czytelnego kodu reprezentuj�cego uk�ad logiczny. Projekt mo�e by� opisany na wielu poziomach abstrakcji, dzi�ki czemu programista ma du�� swobod� i elastyczno�� w tworzeniu konfiguracji FPGA. J�zyk umo�liwia kreowanie i �adowanie zewn�trznych bibliotek, a tak�e realizacj� modu��w, kt�re mog� by� wielokrotnie wykorzystywane w projekcie (struktura hierarchiczna). Wi�kszo�� instrukcji wykonywana jest r�wnolegle, jednak�e istniej� sposoby na stworzenie kodu wykonywanego sekwencyjnie (tzw. procedury) wraz z instrukcjami warunkowymi i p�tlami znanymi z klasycznych j�zyk�w programowania.

Du�� zalet� tej technologii jest uniezale�nienie opisu uk�adu od wyboru konkretnego uk�adu, w jakim b�dzie on p�niej realizowany. Dzi�ki przeno�no�ci istnieje mo�liwo�� symulowania i testowania projektu w wielu �rodowiskach, co u�atwia znalezienie potencjalnych b��d�w. Uk�ad mo�na podda� syntezie tak�e w dowolnym �rodowisku do projektowania FPGA.

Niestety, mo�liwo�� tworzenia projektu na wysokim poziomie abstrakcji niesie za sob� pewne konsekwencja. Narz�dzia do syntezy czasem tworz� nieoptymaln� implementacj�. Jest to cz�sto win� samego projektanta, kt�ry tworzy kod niezgodny z przyj�tymi konwecjami. Co wi�cej, niedo�wiadczony programista mo�e napisa� kod, kt�ry w og�le nie jest syntezowalny. Z drugiej strony - sama idea tworzenia uk�adu cyfrowego na podstawie opisu w j�zyku HDL powoduje przyj�cie pewnych standard�w przez kompilator i generowanie nieoptymalnych rozwi�za� w przypadku niecodziennych konstrukcji.

## 3.6. Implementacja 

Implementacja to pe�en proces stworzenia uk�adu cyfrowego odpowiadaj�cego naszym oczekiwaniom. W jego wyniku otrzymujemy poprawn� konfiguracj�, kt�r� mo�na zaprogramowa� uk�ad FPGA i uruchomi� w pe�ni dzia�aj�ce urz�dzenie. Poszczeg�lne etapy implementacji to:

1. Zdefiniowanie za�o�e� i wymaga� projektowych,
1. Opisanie projektu w j�zyku typu *HDL*,
1. Symulacja kodu �r�d�owego,
1. Synteza, optymalizacja i dopasowanie projektu,
1. Symulacja modelu dopasowanego i zrealzowanego projektu,
1. Zaprogramowanie uk�adu.

### 3.6.1. Zdefiniowanie za�o�e� i wymaga� projektowych
Ka�dy projekt techniczny musi zacz�� si� od zdefniowania konkretnych za�o�e�. Nie inaczej jest w trakcie projektowania system�w cyfrowych. Nale�y zdefiniowa� wymagania, szczeg�lnie dotycz�ce:

* cz�stotliwo�ci dzia�ania uk�adu,
* czas�w ustawiania i propagacji sygna��w,
* �cie�ek krytycznych.

Jasne sprecyzowanie wymaga� u�atwia dob�r narz�dzi oraz konkretnych uk�ad�w, w kt�rych projekt zostanie zaimplementowany.

### 3.6.2. Opisanie projektu w j�zyku typu *HDL*
Zalecane s� 3 metody projektowania:

* zst�puj�ca (top-down),
* wst�puj�ca (bottom-up),
* pozioma.

W omawianym projekcie zosta�a wykorzystana pierwsza z nich. Polega na podzieleniu projektu na funkcje sk�adowe, maj�ce okre�lone, specyficzne wej�cia i wyj�cia oraz realizuj�ce odpowienie funkcje. Modu� na najwy�szym stopniu hierarchii spaja wszystkie elementy i umo�liwia �atw� analiz� dzia�ania uk�adu. Takie podej�cie jest szczeg�lnie korzystne przy tworzeniu skomplikowanych system�w. Oprogramowanie do projektowania uk�ad�w FPGA umo�liwia realizacj� wielopoziomowych struktur.

Po stworzeniu blok�w sk�adowych projektu nale�y przej�� do zakodowania funkcjonalno�ci ka�dego z nich. 

### 3.6.3. Symulacja kodu �r�d�owego
�rodowiska do projektowania umo�liwiaj� przeniesienie fazy symulacji i testowania do wczesnych etap�w tworzenia systemu. Jest to tzw. "symulacja behawioralna", kt�ra obrazuje zachowanie uk�adu opisanego j�zykiem HDL bez uwzgl�dnienia wp�ywu syntezy oraz poprowadzenia po��cze�. Mo�na zaobserwowa� podstawowe zachowanie zrealizowanego projektu, jednak�e bez tak kluczowych czynnik�w, jak np. op�nienia i czasy propagacji.

### 3.6.4. Synteza, optymalizacja i dopasowanie projektu
#### Synteza 
Synteza to proces, w wyniku kt�rego z abstrakcyjnego kodu HDL tworzona jest lista po��cze� mi�dzy blokami realizuj�cymi odpowiednie funkcje logiczne lub zbi�r r�wna� boolowskich. Rezultat tej operacji jest zale�ny od konkretnej technologii, gdy� powinien by� dopasowany do konkretnego modelu uk�adu FPGA, w kt�rym projekt b�dzie implementowany. 

#### Optymalizacja
Proces optymalizacji jest zale�ny od trzech czynnik�w:

* postaci wyra�e� boolowskich,
* rodzaju dost�pnych zasob�w sprz�towych,
* ogranicze� projektowych (**ang. constraints**).

Narz�dzia do optymalizacji umo�lwiaj� wykorzystanie specyficznych w�a�ciow�ci uk�adu konkretnego producenta w celu zapewnienia najlepszych parametr�w wynikowego projektu. Aby tego dokona� mog� korzysta� z przekszta�ce� r�wna� boolowskich otrzymanych w wyniku syntezy, aby dokona� optymalnej realizacji. Ograniczenia projektowe narzucone przez u�ytkownika lub wprowadzone automatycznie umo�liwiaj� efektywniejsz� optymalizacj� pod k�tem wykorzystania dost�pnych zasob�w.

#### Rozmieszczenie i poprowadzenie po��cze�
Proces ten ma ogromny wp�yw na jako�� zrealizowanego uk�adu. Bardzo istotnym parametrem jest czas propagacji sygna��w, na kt�ry kluczowy wp�yw ma spos�b poprowadzenia po��cze�, gdy� to one w�a�nie wprowadzaj� najwi�ksze op�nienia. Programy najwy�szej klasy umo�liwiaj� wykorzystanie blok�w logicznych le��cych blisko siebie, dzi�ki czemu �cie�ki po��czeniowe s� bardzo kr�tkie - w szczeg�lno�ci te, kt�rych op�nienie wp�ywa w krytyczny spos�b na parametry uk�adu. 

### Symulacja modelu dopasowanego i zrealzowanego projektu
Dokonanie symulacji bez syntezy uk�adu umo�liwia dokonanie wst�pnej obserwacji sygna��w. Jednak�e dopiero przesymulowania uk�adu po syntezie i rozmieszczeniu w strukturze FPGA oddaje pe�ny obraz zachowania rzeczywistego projektu. Dzi�ki niej mo�emy przeprowadzi� nie tylko analiz� funkcjonaln�, lecz tak�e sprawdzi� parametry czasowe, op�nienia propagacji sygna��w zegarowych i mi�dzyrejestrowych. 

### 3.6.5. Zaprogramowanie uk�adu
Finalny etapem realizacji projektu jest zaprogramowanie uk�adu. Dokonuje si� go przy pomocy zewn�trznego urz�dzanie jakim jest programator wykorzystuj�cy najcz�ciej standard JTAG.

# 4. System sterowania nadajnikami
## 4.1. Za�o�enia

## Usprawnienia dotychczasowego systemu??

Najwa�niejszym celem pracy in�ynierskiej jest usprawnienie i rozszerzenie funkcjonalno�ci om�wionego wcze�niej systemu, kt�ry mimo i� dzia�a� bardzo dobrze, nie by� pozbawiony wad. G��wnym problemem, kt�ry pojawia� si� w trakcie eksploatacji, by� brak mo�liwo�ci szybkiej zmiany parametr�w systemu. Ka�dy z nadajnik�w posiada� zintegrowany uk�ad CPLD, w kt�rego pami�ci zapisane zosta�y prametry konfiguracyjne. Rozwi�zanie to jest bardzo wygodne z punktu widzenia konstruktora - tworzymy kilka takich samych uk�ad�w, kt�re r�ni� si� tylko bitami zapisanymi w pami�ci. Jednak�e drobna zmiana parametr�w wymaga programowania ka�dego z uk�ad�w oddzielnie. Dodatkowo, poniewa� gniazdo JTAG zosta�o dodatkowo umieszczone w trudno dost�pnym miejscu - nie jest to proces �atwy. Ponadto dla ka�dej z konfiguracji CPLD nale�y przeprowadzi� syntez� uk�adu, co powodowa�o du�e nak�ady czasowe. Taki proces uniemo�liwia� wr�cz przeprowadzanie wydajnych eksperyment�w ze wzgl�du na:

* czas dokonywanych zmian,
* problemy z programowaniem ka�degu uk�adu z osobna.

Istotnym problemem by�a tak�e niedoskona�a sekwencja bit�w przesy�ana w ��czu radiowym. Bit�w steruj�cych by�o zbyt ma�o, a preambu�a ka�dego z pakiet�w nie spe�nia�a do ko�ca swojej roli. Przetwornik A/C umieszczony w p�tli ARW wymaga d�u�szej sekwencji taktowanej wy�szym zegarem. Powi�kszenie liczby bit�w poprawia tak�e precyzj� dekodowania sekwencji w odbiorniku.

`odniesienie do opisu we wst�pie na temat roli preambu�y i przetwornika a/c`

W zwi�zku z tymi problemami zdecydowano si� wprowadzi� udoskonalenia, kt�re zlikwiduj� wy�ej wymienione b��dy przy jednoczesnym zachowaniu wszystkich funkcji uk�adu

Jednym z mo�liwych rozwi�za� jest wprowadzenie centralnego uk�adu steruj�cego  kt�ry zapewni:

* sterowanie sekwencyjnym uruchamianiem nadajnik�w UWB,
* mo�liwo�� ustawienia parametr�w konfiguracyjnych uk�adu w jednym miejscu,
* �atw� rozbudow� i skalowalno��,

W omawianej koncepcji rol� centralnego sterownika pe�ni uk�ad FPGA wraz z odpowiedni� konfiguracj� oraz uk�adami wej�cia-wyj�cia, kt�re zostan� przedstawione w kolejnych rozdzia�ach. 

## 4.2. Architektura systemu
Modyfikacja systemu wymaga�a opracowania nowej architektury, kt�ra wyeliminuje problemy powsta�e w poprzedniej realizacji. Zdecydowano o zmianie po��czenia pier�cieniowego nadajnik�w na rzecz po��czenia w gwiazd� wraz z centralnym uk�adem steruj�cym.

Takie po��cznie posiada zdecydowanie wi�cej zalet, kosztem niewielkiej komplikacji uk�adu. Do ka�dego z nadajnik�w mo�na wysy�a� niezale�nie i sekwencyjnie (b�d� r�wnolegle) sygna�y, kt�rych parametry ustawia si� w sterowniku. Ka�dy z modu��w radiowych otrzymuje sygna� zegarowy bezpo�rednio ze sterownika, dzi�ki czemu system jest niezale�ny od jitteru wprowadzanego przez ka�de z urz�dze� (jitter nie kumuluje si�, tak jak w poprzedniej wersji).

`img:archSystemu`
`dok�adniejszy opis`

Pogl�dow� architektur� systemu zaprezentowano na rysunku `img:archSystemu`. Uk�ad FPGA pe�ni g��wn� funkcj� steruj�c�. Operator systemu `mo�e ustawia� parametry` oraz wyzwoli� dzia�anie systemu. Sterownik generuje odpowiednie sygna�y `(zgodnie z ustawieniami)` wysy�aj�c je na wyj�cia, po czym nast�puje konwersja standardu przesy�ania danych do potrzeb linii transmisyjnych oraz odbiornik�w. Z konwertera sygna�y przesy�ane s� kablami w standardzie Cat 5e (skr�tka - 4 pary symetryczne) do rozdzielaczy, gdzie s� przekazywane do odpowiednich nadajnik�w.

## 4.3. Modu� FPGA
`zdj�cie p�ytki FPGA`
`schemat`
`kr�tki opis`

## 4.4. Modu� konwertera CMOS - LVDS
Uk�ad FPGA Spartan3 firmy Xilinx posiada wyj�cia w r�nych standardach. Najbardziej uniwersalnym jest CMOS, w kt�rym:

* stan wysoki => 3,3V b
* stan niski => 0V

Taki spos�b kodowania stan�w logicznych jest bardzo dobry dla uk�ad�w pracuj�cych blisko siebie z kr�tkimi po��czeniami. Jednak�e przy przesy�aniu sygna��w d�ugimi kablami nie zdaje on egzaminu, gdy� jest bardzo wra�liwy na zak��cenia elektromagnetyczne. Ponadto wyj�cia uk�adu nie s� dopasowane do obci��enia impedancj� linii transmisyjnej.

W zwi�zku z tym zdecydowano, i� do transmisji sygna��w steruj�cych zostanie wykorzystany r�nicowy standard przesy�ania danych LVDS, opisany w `dodatku 9.1`. Mimo i� sam uk�ad FGPA Spartan3 posiada wyj�cia w tym standardzie, to nie mo�na ich wykorzysta� ze wzgl�du na brak kompensacji d�ugo�ci wszystkich �cie�ek na p�ytce. Konwerter sygna��w zosta� zrealizowany jako modu� na oddzielnej p�ytce drukowanej ze z��czem umo�liwiaj�cym �atwe do��czenie do bazowego systemu z uk�adem FPGA.

`img:pcbSchemat`

Do konwersji wykorzystano uk�ady MAX9157 firmy Maxim, kt�re (na podstawie `bibl:datasheetMAX9517`):

* obs�uguj� cztery kana�y transmisji CMOS -> LVDS lub LVDS -> CMOS,
* umo�liwiaj� transmisj� strumieni o przep�ywno�ci do 200Mbps,
* odbieraj� sygna�y r�nicowe o poziomach ju� od 100mV,
* posiadaj� obwody zabezpieczaj�ce wyj�cie przed niepo��danym stanem na wej�ciu (fail-save input receiver),
* umo�liwiaj� pod��czania i od��czanie w trakcie pracy uk�adu (hot-swappable).

Mo�liwo�ci te sprawiaj�, �e uk�adu MAX9157 s� bardzo dobrymi elementami do budowy interfejs�w do przesy�ania danych d�ugimi kablami.

![Schemat zasilania](./img/zasilanie.png "img:zasilanie")

Ze wzgl�du na du�y pob�r pr�du przez nadajniki ca�y system nie mo�e zosta� zasilony przez p�ytk� z modu�em FPGA. Zdecydowano o zastosowaniu dodatkowego zasilacza, kt�ry dostarczy odpowiedniej mocy do konwertera oraz nadajnik�w (co zosta�o zobrazowane na rysunku `img:zasilanie`). Do wolnej pary (do transmisji danych wykorzystano tylko 3 z 4 par) pod��czone zostanie napi�cie zasilania oraz masa. Potencja�y te s� pod��czone z obu rozdzielaczy jednocze�nie i s� po��czone poprzez diody oraz filtry z�o�one z kondensatora i d�awika, kt�rego celem jest odfiltrowanie wszelkich zak��ce� oraz separacja potencja��w analogowych i cyfrowych (aVcc, aGnd, Vcc, cGnd).

`img:pcbLayout`

Zaprezentowany na rysunku `img:pcbLayout` layout p�ytki zosta� stworzony w programie Altium Designer 6. Rozmieszczenie wyprowadze� w uk�adach MAX9157 jest bardzo przyjazne dla konstruktura i u�atwia prowadzenie �cie�ek (wej�cia po jednej stronie, wyj�cia po drugiej, przeci�cie p�aszyczyny masy idealnie w po�owie uk�adu). Mimo to nie oby�o si� bez problem�w z poprowadzeniem zasilania, co wymusi�o dolutowanie zwor do p�ytki.

`img:pcbPhoto`

Uruchamianie uk�adu konwertera przebieg�o bez wi�kszych problem�w. Pierwszym krokiem by�o sprawdzenie doprowadze� zasilania poprzez pod��czenie napi�cia sta�ego do �cie�ek rozprowadzaj�cych je po uk�adzie. Napi�cie na wyj�ciu stabilizatora wynios�o 3.3V. Nast�pnie pod��czono konwerter do modu�u z FPGA oraz rozdzielacze do wyj�cia. Na oscyloskopie zaobserwowano przebiegi sygna��w r�nicowych, jednak�e ze wzgl�du na rozwarcie na ko�cu linii by�y one zniekszta�cone. Dopiero pod��czenie dopasowanych generator�w umo�liwi�o obserwacj� poprawnych sygna��w.


## 4.5. Struktura generowanych sygna��w ##

### 4.5.1. Struktura pakietu ###
System lokalizacyjny, do realizacji swoich funkcji, wykorzystuje sekwencje sygna��w przesy�anych w ��czu radiowym. Nadajniki przesy�aj� zestandaryzowane sekwencje bit�w, kt�rych ka�de pole sk�adowe reprezentuje wykonanie odpowiednich procedur w odbiorniku. Po detekcji przesy�anej sekwencji odbiornik realizuje funkcj� okre�lon� przez ci�g bit�w. Struktura logiczna przesy�anych danych zosta�a zaprezentowana na rysunku `img:SchPak1`.

![Struktura pakietu](./img/pakiet.png "img:SchPak1")

W schemacie pakietu informacyjnego mo�emy wyr�ni� kilka p�l, kt�re uruchamiaj� odpowiednie funkcje odbiornika. S� to:
* PRMB
* STPS
* BSTP
* IDN
* STRS
* BSTR

Ka�dy z nich odpowiada za inicjalizacj� odpowiedniego procesu w odbiorniku, kt�re po zako�czeniu umo�liwiaj� okre�lenie r�nicy czas�w propagacji sygna��w i finalnie obliczenie pozycji. 

1. **PRMB** - preambu�a. Sk�ada si� z ok. 20 impuls�w. Nie niesie tre�ci informacyjnej, jednak�e jest bardzo istotna z energetycznego punktu widzenia. Umo�liwia bowiem uk�adom odbiornika okre�lenie poziomu sygna�u, z jakim� b�d� transmitowane kolejne bity. Wej�ciowy uk�ad *ARW* (ARW - Automatyczna Regulacja Wzmocnienia) dostosowuje parametry wzmacniacza wej�ciowego do poziomu mocy odebranej preambu�y. Po ustaleniu tych parametr�w odbiornik jest gotowy do odebrania i detekcji kolejnych bit�w, kt�re ju� nios� konkretn� tre�� informacyjn�.
1. **STPS** - odblokowanie zatrzymania pomiaru czasu.
1. **BSTP** - zatrzymanie pomiaru czasu.
1. **IDN** - identyfikator nadajnika. D�ugo�� tego pola (32 bity) wynika ze sposobu realizacji pomiaru przez uk�ady odbiornika. Wykorzystany do pomiaru uk�ad TDC (*Time to Digital Converter*) typu GP2 produkcji firmy Acam wymaga odpowiedniego czasu, aby wystawi� na swoje wyj�cia wynik pomiaru oraz przygotowa� si� do realiazacji kolejnego pomiaru.
1. **STRS** - odblokowanie uruchomienia pomiaru czasu.
1. **BSTR** - uruchomienie pomiaru czasu.

Kr�tkiego wyja�nienia wymaga kolejno�� transmitowanych pakiet�w - najpierw pomiar jest zatrzymywany, a p�niej dopiero uruchamiany. Jest to konsekwencja zastosowanego systemu TDOA, gdzie mierzone s� r�nice czas�w dotarcia sygna��w od poszczeg�lnych nadajnik�w. 

`szczeg�owy opis - rozdzia� o TDOA`

### 4.5.2. Parametry czasowe ###

System transmisyjny oraz charakterystyka kana�u radiowego narzucaj� okre�lone wymagania co do parametr�w parametr�w czasowych przesy�anych sekwencji.

![Odpowied� impulsowa kana�u radiowego - przyk�ad](./img/impulseResponse.gif "img:kanalRadiowy")

Na rysunku `img:kanalRadiowy - rysunek pogl�dowy �ci�gni�ty z internetu` przedstawiono przyk�adow� charakterystyk� odpowiedzi impulsowej kana�u radiowego po pobudzeniu impulsem UWB. Mo�na zauwa�y� kilka charakterystycznych fragment�w. Pierwszy, wyra�ny pik jest sygna�em, kt�ry dotar� bezpo�rednio od nadajnika do odbiornika. Po kr�tkiej przerwie pojawiaj� si� kolejne fragmenty sygna�u, kt�re powsta�y poprzez niekorzystne zjawisko propagacji wielodrogowej (sygna� nadany odbija si� od du�ych (w stosunku do d�ugo�ci fali) obiekt�w i dociera do odbiornika z op�nieniem). Te sk�adowe mog� zaburzy� poprawno�� odbioru, gdy� urz�dzenie odbiorcze nie jest w stanie rozr�ni� impuls�w bezpo�rednich od odbitych. 

W zwi�zku z powy�szym faktem na etapie projektowania sygna��w transmitowanych drog� radiow� nale�y zwr�ci� szczeg�ln� uwag� na odst�p miedzybitowy. Odpowiedni jego dob�r jest kompromisem pomi�dzy czasem dzia�ania systemu (kr�tki odst�p), a uchronieniem si� od sk�adowych wielodrogowych (wi�kszy odst�p). W trakcie bada� poprzedzaj�cych projektowanie systemu stwierdzono, i� dla zak�adanych warunk�w pracy odst�p mi�dzybitowy na poziomie *200-300 \[ns\]* jest ca�kowicie wystarczaj�cy i skutecznie wyeliminuje omawiany problem.

Z okre�lonego odst�pu mi�dzybitowego wynika wprost cz�stotliwo�� z jak� nale�y generowa� impulsy. Zawiera si� ona w przedziale od 3.33  do 5 MHz. Powy�szym rozwa�aniom nie podlega jednak sygna� preambu�y, w kt�rym okres powtarzania impuls�w wynosi *20 \[ns\]*, wobec czego cz�stotliwo�� taktowania uk�ad�w generowania preambu�y wynosi 50 \[MHz\].

### 4.5.3. Modulacja ###

Do przesy�ania danych w ��czu radiowych cz�sto wykorzystuje si� modulacj� *OOK* (OOK - On-Off Keying), kt�rej ide� prezentuj� rysunki `img:OOK1` oraz `img:OOK2`

![Sygna� oryginalny - �r�d�o: National Instruments (www)](./img/OOK_1.gif "img:OOK1")

![Sygna� zmodulowany - �r�d�o: National Instruments (www)](./img/OOK_2.gif "img:OOK2")

Logicznej jedynce odpowiada wys�anie no�nej (lub, tak jak w omawianym przypadku, impulsu UWB). Brak sygna�u to logiczne zero.

W omawianym systemie zastosowano zmodyfikowan� wersj� tej modulacji. W ��czu radiowym transmitowane s� sygna�u UWB, w zwi�zku z czym logicznej jedynce odpowiada generacja impulsu; natomiast logiczne zero to brak nadawania. Zastosowane generatory UWB s� wyzwalane narastaj�cym zboczem sygna�u wej�ciowego. W zwi�zku z tym, nale�y im dostarczy� przebieg wej�ciowy, kt�ry zmieni sw�j stan z 0 na 1 w momencie po��danej generacji. Ma to istotne znaczenie z punktu widzenia kszta�towania sygna��w w uk�adzie FPGA.

# 5. Konfiguracja FPGA 
## 5.1. Wprowadzenie
Opisane w rozdziale `Programowalne uk�ady cyfrowe` struktury FPGA s� bardzo wygodnym narz�dziem do budowania elektronicznych system�w cyfrowych. Dzi�ki mo�liwo�ci zaimplementowania wielu klasycznych element�w (liczniki, rejestry, automaty stan�w) i szerokiej ich rozbudowy mo�na zaprojektowa� nawet bardzo z�o�one uk�ady. Podzia� na struktury hierarchiczne u�atwia zar�wno budowanie uk�adu jak i jego p�niejsz� analiz�.

## 5.2. Interfejs zewn�trzny i opcje konfiguracyjne
`opisanie sterowania uk�adem, brak implementacji p�ki co`
`jakie stany (elektryczne i logiczne) co wyzwalaj�`
`poziomy napi��?`

Sygna�y wej�ciowe | Opis |
-----------------|------|
`clk_in` |  wej�cie sygna�u zegarowego wraz z buforem zapewniaj�cym optymaln� propagacj� sygna�u w uk�adzie |
`start` | uruchomienie uk�adu |
`rst` | reset asynchroniczny |

Sygna�y wyj�ciowe | Opis |
------------------|------|
`wyj�cia` | sze�� wyj�� wygenerowanych sygna��w 

## 5.3. Top module
Na najwy�szym stopniu hierarchii projektu znajduje si� element `top module`. W uk�adzie zdefiniowano wszystkie wymienione wcze�niej wej�cia, wyjscia oraz po��czenia mi�dzy poszczeg�lnymi blokami sk�adowymi. Na rysunku `img:topModule` mo�emy wyr�ni�
* `automat` - kt�ry steruje dzia�aniem pozosta�ych blok�w,
* `trx1..6` - zestaw blok�w generuj�cych sygna�y steruj�ce poszczeg�lnymi nadajnikami,k
* `dzielniki cz�stotliwo�ci` - bloki umo�liwiaj�ce dostosowanie cz�stotliwo�ci sygna�u zegarowego do potrzeb r�nych blok�w funkcjonalnych

### 5.3.1. Automat steruj�cy

![Automat steruj�cy](./img/blok_main_automat.png "img:blokMainAutomat")

Bloki generuj�ce sygna�y s� sterowane przez automat zarz�dzaj�cy, kt�ry:

* czeka na polecenie u�ytkownika do rozpocz�cia generacji,
* uruchamia pierwszy generator,
* czeka na informacj� zwrotn�, po otrzymaniu kt�rej uruchamia kolejny generator
* analogicznie uruchamia kolejne generatory
* `umo�liwia generacj� pojedyncz� lub ci�g��`
* `umo�liwia sterowanie odst�pem mi�dzybitowym`

![Automat steruj�cy](./img/diagram_abstract.png "img:abstractDiagram")

![Automat steruj�cy](./img/diagram_closer.png "img:closerDiagram")

Na pierwszym z powy�szych rysunk�w zaprezentowano diagram stan�w automatu steruj�cego, gdzie ka�dy proces generacji opisano pojedynczym stanem. Drugi z rysunk�w pokazuje fragment pierwszego z uwzgl�dnieniem konkretnych stan�w rzeczywistego automatu. Jest to automat typu Mealy'ego, gdy� wyj�cia uk�adu zale�ne s� nie tylko od aktualnego stanu, ale tak�e od warto�ci logicznej sygna��w wej�ciowych. 

### 5.3.2. Dzielniki cz�stotliwo�ci

![Dzielniki cz�stotliwo�ci](./img/blok_clk_div.png "img:dzieniki")

Ze wzgl�du na r�ne czasy trwania generowanych w uk�adzie nale�a�o wytworzy� sygna�y zegarowe o r�nej cz�stotliwo�ci, przy czym nale�y pami�ta� o zapewnieniu synchronizmu mi�dzy nimi. Aby to osi�gn�� wykorzystano elementy, kt�re podziel� cz�stotliwo�� o odpowiedni� warto��, co skutkuje wyd�u�eniem czasu trwania okresu zegara. 

Proste dzielniki mog� by� wykonane jako z�o�enie kilku przerzutnik�w. W prostym przypadku dzielenia przez 2 implementacja takiego bloku funkcjonalnego sk�ada si� z jednego przerzutnika D oraz negatora wpi�tego w p�tl� sprz�enia zwrotnego do wej�cia D.

![Dzielnik przez 2](./img/blok_clk_div2.png "img:dzienik2")

W bardziej z�o�onych przypadkach warto pos�u�y� si� j�zykiem VHDL, w kt�rym mo�na zaimplementowa� taki blok, kt�rego wsp�czynnik podzia�u b�dzie dowolnie definiowalnym parametrem.

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
Na najwy�szym stopniu hierarchii umieszczonych zosta�o 6 uk�ad�w generuj�cych sygna�y wyzwalaj�ce poszczeg�lne nadajniki. Uk�ady te reprezentuje makroblok o strukturze przedstawionej na rysunku `:img:struktura makrobloku`:

`img:struktura makrobloku`

![Blok automat](./img/blok_automat.png "img:blokAutomat")


Sygna�y wej�ciowe | Opis |
-----------------|------|
clk              | g��wny sygna� zegarowy synchronizuj�cy prac� uk�adu (100 \[MHz\]) |
clk preamb       | sygna� zegarowy taktuj�cy generowanie preambu�y (`ile?`) |
clk data         | sygna� zegarowy taktuj�cy generowanie bit�w informacyjnych  (`ile?`) |
start            | wyzwolenie generacji sekwencji bit�w |
rst              | reset asynchroniczny |


Sygna�y wyj�ciowe | Opis |
-----------------|------|
`out`            | g��wne wyj�cie generowanej sekwencji |
`finish_preamb`  | sygna� informuj�cy o zako�czeniu generacji preambu�y |
`finish`         | sygna� informuj�cy o zako�czeniu generacji ca�ej sekwencji |

Ka�dy z nich posiada bli�niacz� wewn�trzn� struktur�, kt�ra sk�ada si� z:

* zestawu wej��,
* automatu steruj�cego,
* dw�ch licznik�w,
* uk�adu kombinacyjnego,
* multiplekser�w wyj�ciowych.

### 5.4.1. Automat steruj�cy
Prac� makrobloku steruje g��wny automat, kt�ry uruchamia sekwencyjnie kolejne bloki zgodnie z diagramem stan�w przedstawionym na rysunku `img:diagramStanow`.

![Automat steruj�cy](./img/automat.png "img:diagramStanow")

Automat, b�d�c w stanie pocz�tkowym, czeka na wyzwolenie sygna�em start, kt�ry pochodzi z uk�ad�w na wy�szym poziomie hierarchii. Gdy sygna� ten si� pojawi uruchomiona zostaje generacja preambu�y.

Za proces ten odpowiada licznik `cnt_20`, kt�ry jest taktowany zegarem 50 \[MHz\], co odpowiada cz�stotliwo�ci sygna�u preambu�y. Uruchomienie licznika powoduje wys�anie na wyj�cie `preamb` sygna�u o tej w�a�nie cz�stotliwo�ci. Wyj�ciowy multiplekser jest w stanie "0, czyli sygna� preambu�y pojawia si� na wj�ciu `out` makrobloku. 

Po przepe�nieniu licznika `cnt_20` wysy�any jest impuls potwierdzaj�cy do g��wnego automatu. Zmiana stanu rozpoczyna kolejny proces - generacj� sekwencji informacyjnej - poprzez uruchomienie licznika `cnt_72`, kt�rego stan adresuje uk�ad ROM. Odpowied� `uk�adu pami�ciowego` przechodzi przez multipleksery wyj�ciowe (opisane w rozdziale 5.4.3), a nast�pnie sekwencja jest wystawiana na wyj�cie ca�ego makrobloku.

### 5.4.2. ROM 

Sekwencje informacyjne, przesy�ane do poszczeg�lnych nadajnik�w, s� r�ne i musi by� zapisana w konfiguracji uk�adu. Nale�a�o zatem wprowadzi� element, kt�ry przechowywa�by dane oraz umo�liwia� w �atwy spos�b ich ewentualn� zmian�.

Rozwa�ano zastosowanie specyficznych dla uk�ad�w z rodziny Xilinx Spartan3 rozwi�za�, kt�re umo�liwiaj� wygenerowanie w strukturze FPGA pami�ci typu *Read Only Memory*. Jednak�e, ze wzgl�du na ma�� uniwersalno�� takiej realizacji, zdecydowane o stworzeniu prostszej i bardziej "przeno�nej" implementacji. Zamiast pami�ci ROM u�yto klasycznego uk�adu kombinacyjnego w postaci tablicy prawdy. Jej opis w j�zyku VHDL nadaje uniwersalno�ci i pozwala przeprowadzi� syntez� dla dowolnych uk�ad�w FPGA.

![Blok ROM](./img/blok_rom.png "img:blokRom")

Z punktu widzenia zacisk�w wej�ciowych i wyj�ciowych uk�ad zachowuje si� identycznie jak pami�� ROM.

#### Generator tablicy prawdy

Przeno�no�� powy�szego rozwi�zania osi�gni�ta przez realizacj� w j�zyku VHDL poci�ga za sob� ma�� czytelno�� kodu (dla osoby nieznaj�cej tej technologii) oraz �mudny proces zmiany warto�ci, je�li zajdzie taka konieczno��. Aby u�atwi� edycj� parametr�w stworzono prosty program w j�zyku Java, kt�ry umo�liwia automatyczne wygnerowanie pliku VHDL opisuj�cego dan� tablic� prawdy.

![Program JAVA - generator VHDL](./img/java_program.png "img:generatorVHDL1")

Po uruchomieniu programu wystarczy uzupe�ni� pola:
* `entity` - nazwa danego bloku,
* warto�ci bit�w ka�dego z blok�w,
* nazwa pliku.

Naci�ni�cie przycisku `generuj` utworzy w katalogu programu plik opisuj�cy tablic� prawdy z ustawionymi przez u�ytkownika parametrami.

![Efekt pracy generatora](./img/java_plik_wygnerowany.png "img:generatorVHDL2")

### 5.4.3. Multipleksery wyj�ciowe
Zapewnienie generacji impulsu przy ka�dym wyst�pieniu jedynki logicznej wymaga odpowiedniego zakodowania sygna�u na wyj�ciu uk�adu FPGA - ka�dej jedynce musi odpowiada� narastaj�ce zbocze. Zrealizowanie takiego kodowania jest mo�liwe na kilka sposob�w.

W pierwszym podej�ciu po��czono wyj�cie informacyjne z sygna�em zegarowym o odpowiedniej cz�stotliwo�ci zwyk�� bramk� AND. Z punktu widzenia logiki boolowskiej oraz symulacji behawioralnych rozwi�zanie to jest poprawne. W rzeczywistym uk�adzie jednak powodowa�o to pewne problemy - na wyj�ciu bramki pojawia�y si� "szpilki" w trakcie opadaj�cego zbocza zegarowego, kt�re mog�yby wyzwoli� generatory UWB.

W zwi�zku z tym zast�piono bramk� AND multiplekserem przystosowanym do prze��czania sygna��w zegarowych (specyficznego dla uk�adu Spartan3). 

`rysunek!!!!`


### Realizacja regulacji przesuni��

### Testowanie

## Interfejs 

# 6. Badania

## Cel i zakres bada�
Celem bada� jest weryfikacja realizacji projektu pod k�tem zdefiniowanych wcze�niej wymaga�. Nale�y sprawdzi�, czy parametry okre�lone we wst�pnych za�o�eniach spe�niaj� okre�lone kryteria. Opisane w `rozdziale 5.5` symulacje potwierdzaj� zgodno�c z za�o�eniami, jednak�e pe�n� warto�� projektu mog� odda� tylko rzeczywiste pomiary.

## Uk�ad pomiarowy 

Uk�ad pomiarowy sk�ada si� z:

* pe�nego systemu sterownika opracowanego w ramach pracy,
* p�ytki konwertera standardu LVDS -> LVPECL,
* oscyloskopu pr�bkuj�cego TexasInstruments TDS8200.

`rysunek`

P�ytka konwertera LVDS->LVPECL oparta zosta�a na uk�adach MAX9375. Standard LVPECL (Low Voltage Positive Emmiter-Coupled Logic) umo�liwia dystrybucj� bardzo szybkich sygna��w cyfrowych w liniach 50 `omowych`.

## Metodyka pomiar�w

Przeprowadzenie dok�adnych bada� parametr�w czasowych wymaga synchronizacji wyzowlenia oscyloskopu z badanym sygna�em. Aby zapewni� spe�nienie tego warunku dokonano niewielkiej modyfikacji uk�adu wyprowadzaj�c jeden z wewn�trznych sygna��w do wyj�cia uk�adu FGPA. Sygna� ten jest zsynchronizowany z pocz�tkiem cyklu generacji pakiet�w, w zwi�zku z czym mo�e zosta� u�yty do wyzwolenia oscyloskopu.

`rysunek - paczka i wyzwolenie`

Po zsynchronizowaniu oscyloskopu realizowano pomiary poprzez standardowe funkcje dost�pne w cyfrowych urz�dzeniach pomiarowych, takie jak *marker*, *delta marker*, *burst width measure* itd.

## Pomiar parametr�w czasowych sygna��w

### Szeroko�� paczki (burst width)

### Szeroko�� preambu�y 

### Szeroko�� impulsu

### Odst�p mi�dzybitowy

## Pomiar parametru jitter

W systemach okre�laj�cych bardzo dok�adnie pozycj� istotnym parametrem jest jitter. Niewielkie wahania momentu wyzwolenia sygna�u mo�e powodowa� du�y b��d dok�adno�ci okre�lenia pozycji (`opisane w rozdziale o lokalizacji uwb`). St�d wynika rygorystyczne wymaganie na ten parametr.

`metodyka badania jittera`

Na pocz�tku zbadano jitter samego zegara umieszczonego na p�ytce z modu�em FPGA, kt�rego du�a warto�� stawia�aby pod znakiem zapytania sens stosowania takiego modu�u w sterowniku. Zbadano sygna�, kt�rym taktowane jest generowanie sekwencji danych (tj. zegar g��wny po podzieleniu przez 10) i otrzymano warto�� 10 [ps], co mo�na uzna� za bardzo dobr�. Kolejne modu�y b�d� do tej warto�ci dodawa� sw�j jitter.

`jaki jitter ma max9157 i max9375 (2ps RMS)`

# 7. Podsumowanie

# 8. Bibliografia
* `bib:LVDS` Low-Voltage Differential Signaling, International Engineering Consortium, 
* `bibl:praca p.Kosi�skiego` - praca magisterska 
* `bibl:datasheetMAX9517`
* `bibl:VHDL` J�zyk VHDL - Kevin Skahill
* `bibl:spartan` Xilinx Spartan 3 FPGA Datasheet

# 9. Dodatki
## 9.1. Standard LVDS

Do transmisji danych w kablach doprowadzaj�cych sygna�y do generator�w stosowany jest standard LVDS `(rys. img:LVDS)`. Jest to r�nicowy spos�b transmisji danych, gwarantuj�cy:

* wysok� energooszcz�dno��,
* wysok� przep�ywno��,
* ochron� przed zak��ceniami elektromagentycznymi.

![Standard LVDS - �r�d�o: National Instruments (www)](./img/lvds.png "img:LVDS")

`bib:LVDS` R�nicowy standard transmisji polega na wykorzystaniu dw�ch skr�conych �y� jako linii sygna�owych (o dw�ch r�nych polaryzacjach) zamiast po jednej sygna�owej i masy. Nadajnik wymusza przep�yw pr�du o ma�ym nat�eniu (zazwyczaj *i = 3.5 \[mA\]*), kt�ry w odbiorniku przep�ywa przez rezystor dopasowuj�cy wej�cie do linii transmisyjnej (zazwyczaj *R = 100 - 150 \[ohm\]*). Pierwszym stopniem odbiornika jest wzmacniacz o wej�ciu r�nicowym o du�ym wzmocnieniu sk�adowej r�nicowej, co zapewnia poprawny odbi�r niewielkich sygna��w. Ponadto takie uk�ady posiadaj� du�e t�umienie sk�adowej wsp�lnej (sumacyjnej), co sprawia, �e wyst�puj�ce w obu liniach sygna�owych jednocze�nie zak��cenia elektromagnetyczne, nie maj� wp�ywu na poprawno�� odebranego sygna�u.




