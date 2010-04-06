# Wstęp #

# Wprowadzenie do dziedziny #

# Opis rozwiązania #

## Usprawnienia istniejącego systemu ##

### Dotychczasowe działanie ###

**TODO: Opis systemu. Jakiś wstęp**.

Opracowany system składa się z z pięciu nadajników (układ cyfrowy CPLD, generator UWB oraz antena) połączonych w szeregowo. Pierwszy z nich jest nadajnikiem nadrzędnym, który:

* decyduje o rozpoczęciu procesu generacji i wysyłaniu impulsów w łączu radiowym,
* uruchamia kolejny nadajnik.




### Problem ###

System w swojej dotychczasowej wersji działał bardzo dobrze, lecz nie był pozbawiony wad. Głównym problemem, który pojawiał się w trakcie eksploatacji, był brak możliwości szybkiej zmiany parametrów systemu. Każdy z nadajników systemu posiadał zintegrowany układ CPLD, w którego pamięci zapisane zostały prametry konfiguracyjne. Rozwiązanie to jest bardzo wygodne z punktu widzenia konstruktora - tworzymy kilka takich samych układów, które różnią się tylko bitami zapisanymi w pamięci. Jednakże drobna zmiana parametrów wymaga programowania każdego z układów oddzielnie. Jeśli gniazdo JTAG zostało dodatkowo umieszczone w trudno dostępnym miejscu - nie jest to proces łatwy. Ponadto dla każdej z konfiguracji CPLD należy przeprowadzić syntezę układu, co powodowało duże nakłady czasowe. Taki proces uniemożliwiał wręcz przeprowadzanie wydajnych eksperymentów ze względu na:

* czas dokonywanych zmian
* problemy z programowaniem każdegu układu z osobna

W związku z tymi problemami zdecydowano się wprowadzić udoskonalenia, które zlikwidują wyżej wymienione błędy przy jednoczesnym zachowaniu wszystkich funkcji układu

### Jak można poprawić? ###

#### Ogólnie ####

Jednym z możliwych uproszczeń systemu jest wprowadzenie centralnego układu nadzorującego, który zapewni:

* sterowanie sekwencyjnym uruchamianiem nadajników UWB
* możliwość ustawienia parametrów konfiguracyjnych układu w jednym miejscu
* łatwą rozbudowę i skalowalność


#### W mojej koncepcji ####

## Założenia programu ##

## Struktura generowanych sygnałów ##

## Układ FPGA ##

## Interfejs ##


# Badania programu #
![Alt text](./img/Praca_Inżynierska.png)


