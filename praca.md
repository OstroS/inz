# Wstęp #

# Wprowadzenie do dziedziny #

# Opis rozwiązania #

## Usprawnienia istniejącego systemu ##

### Dotychczasowe działanie ###

`Wstęp`

Opracowany system składa się z z pięciu nadajników (układ cyfrowy CPLD, generator UWB oraz antena) połączonych w szeregowo. Pierwszy z nich jest nadajnikiem nadrzędnym, który:

* decyduje o rozpoczęciu procesu generacji i wysyłaniu impulsów w łączu radiowym,
* uruchamia kolejny nadajnik.

Każdy z nadajników, po otrzymaniu sekwencji sterującej, wysyła impulsy w łączu radiowym, które sterują pracą odbiornika. Odpowiednie sekwencje uruchamiają i zatrzymują pomiar czasu, a także niosą treść informacyjną umożliwiającą zidentyfikowanie konretnego nadajnika. Odbiornik, zgodnie ze sposobem działania systemów typu TDOA, mierzy różnicę czasów pomiędzy otrzymaniem sygnałów z poszczególnych nadajników. Po wysłaniu sekwencji z ostatniego nadajnika pomiar się kończy i odbiornik przechodzi do obliczania pozycji korzystając z zaprogramowanych algorytmów.

`Dokładniejszy opis`

### Problem ###

System w swojej dotychczasowej wersji działał bardzo dobrze, lecz nie był pozbawiony wad. Głównym problemem, który pojawiał się w trakcie eksploatacji, był brak możliwości szybkiej zmiany parametrów systemu. Każdy z nadajników systemu posiadał zintegrowany układ CPLD, w którego pamięci zapisane zostały prametry konfiguracyjne. Rozwiązanie to jest bardzo wygodne z punktu widzenia konstruktora - tworzymy kilka takich samych układów, które różnią się tylko bitami zapisanymi w pamięci. Jednakże drobna zmiana parametrów wymaga programowania każdego z układów oddzielnie. Jeśli gniazdo JTAG zostało dodatkowo umieszczone w trudno dostępnym miejscu - nie jest to proces łatwy. Ponadto dla każdej z konfiguracji CPLD należy przeprowadzić syntezę układu, co powodowało duże nakłady czasowe. Taki proces uniemożliwiał wręcz przeprowadzanie wydajnych eksperymentów ze względu na:

* czas dokonywanych zmian,
* problemy z programowaniem każdegu układu z osobna.

W związku z tymi problemami zdecydowano się wprowadzić udoskonalenia, które zlikwidują wyżej wymienione błędy przy jednoczesnym zachowaniu wszystkich funkcji układu

### Jak można poprawić? ###

Jednym z możliwych uproszczeń systemu jest wprowadzenie centralnego układu sterującego  który zapewni:

* sterowanie sekwencyjnym uruchamianiem nadajników UWB,
* możliwość ustawienia parametrów konfiguracyjnych układu w jednym miejscu,
* łatwą rozbudowę i skalowalność.

W omawianej koncepcji rolę centralnego sterownika pełni układ FPGA wraz z odpowiednią konfiguracją oraz układami wejścia-wyjścia, które zostaną przedstawione w kolejnych rozdziałach. 

## Założenia programu ##

`TODO later`

## Struktura generowanych sygnałów ##

### Przekaz informacyjny ###
System lokalizacyjny, do realizacji swoich funkcji, wykorzystuje sekwencje sygnałów przesyłanych w łączu radiowym. Nadajniki przesyłają zestandaryzowane sekwencje bitów, których każde pole składowe reprezentuje wykonanie odpowiednich procedur w odbiorniku. Po detekcji przesyłanej sekwencji odbiornik realizuje funkcję określoną przez ciąg bitów. Strukturę logiczną przesyłanych danych prezentuje rysunek `:SchPak1`.

`:SchPak1 schemat pakietu`

### Funkcje bitów ###
W schemacie pakietu informacyjnego możemy wyróżnić kilka pól, które uruchamiają odpowiednie funkcje odbiornika. Są to:
* PRMB
* STPS
* BSTP
* IDN
* STRS
* BSTR

`(rozwinięcia skrótów po angielsku)`
Każdy z nich odpowiada za inicjalizację odpowiedniego procesu w odbiorniku, które po zakończeniu umożliwiają określenie różnicy czasów propagacji sygnałów i finalnie obliczenie pozycji. 

`Opisać rolę każdego fragmentu pakietu`

1. **PRMB** - preambuła. Składa się z ok. 20 impulsów nadawanych z częstotliwością 50 MHz. Nie niesie treści informacyjnej, jednakże jest bardzo istotna z energetycznego punktu widzenia. Umożliwia bowiem układom odbiornika określenie poziomu sygnału, z jakimś będą transmitowane kolejne bity. Wejściowy układ *ARW* (ARW - Automatyczna Regulacja Wzmocnienia) dostosowuje parametry (`jakie? czy tylko wzmocnienie, czy może coś jeszcze?`) wzmacniacza wejściowego do poziomu mocy odebranej preambuły. Po ustaleniu tych parametrów odbiornik jest gotowy do odebrania i detekcji kolejnych bitów, które już niosą konkretną treść informacyjną.
1. **STPS** - odblokowanie zatrzymania pomiaru czasu.
1. **BSTP** - zatrzymanie pomiaru czasu.
1. **IDN** - identyfikator nadajnika.
1. **STRS** - odblokowanie uruchomienia pomiaru czasu.
1. **BSTR** - uruchomienie pomiaru czasu.

### Parametry czasowe ###

`odstęp międzybitowy, częstotliwość zegara, przepływność`

System transmisyjny oraz charakterystyka kanału radiowego narzucają określone wymagania co do parametrów parametrów czasowych przesyłanych sekwencji.

## Układ FPGA ##

## Interfejs ##


# Badania programu #


