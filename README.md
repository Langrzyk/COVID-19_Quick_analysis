# W Obliczu COVID-19
Analiza danych o COVID-19 w ramach kursu Korona Science

Jest to przejrzysty projekt pozwalający na szybką analizę obecnej sytuacji związanej z Koronawirusem na świecie jak i w Europie. Postanowiłam dokonać porównania przebiegu Koronawirusa w Polsce i w dowolnym innym dotkniętym tym problemem kraju na świecie. Zależało mi na głównie na przejrzystym i dobrze dopracowanym kodzie zamkniętym w funkcje czyniące go uniwersalnym pod względem wyboru Krajów do porównania, i aby to porównanie było jak najbardziej przejrzyste oraz dawało jasne i zrozumiałe wyniki. Uważam, że porównanie sytuacji w Polsce z pozostałymi krajami dotkniętymi COVID-19 pozwoli nakreślić skalę problemu, jak również umożliwi określenie pozycji Polski na tle pozostałych państw, które tak jak nasz Kraj zmagają się z Koronawirusem i starają się mu przeciwdziałać. 

### Dane i przygotowanie
Dane wykorzystane podczas analizy pochodzą z następujących źródeł:
- Codziennie aktualizowane dane o [wykrytych przypadkach COVID-19](https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv)
- Codziennie aktualizowane dane o [przypadkach śmierci z powodu COVID-19](https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_deaths_global.csv)
- Codziennie aktualizowane dano o [przypadkach wyleczenia z COVID-19](https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_recovered_global.csv)

Przed wykonaniem wizualizacji, należało dokonać analizy i przygotować dane. Stworzyłam więc dwie funkcje odpowiedzialne za uporządkowanie potrzebnych informacji i takie ich przygotowanie aby wizualizacja nie sprawiała trudności. 

Funkcje te realizują następujące czynności:
- `onlyCountry(raw_data)` - Tworzy DataFrame bez podziału na prowincje czy
stany. W mojej analizie taki podział jest zbędny, gdyż ograniczam się do analizy kraju
jako całości. Funkcja ta jest szczególnie przydatna przy wizualizacji danych na mapach.
-  `dataclean(raw_data)` – Tworzy DataFrame z jedną kolumną „Cases”,
indeksowaną przez nazwę kraju i datę. Funkcja ta jest szczególnie przydatna przy
porównaniu Polski z innymi krajami.

### Aktualny stan COVID-19 na świecie i w Europie

Najbardziej przejrzysty obraz aktualnego stanu na świecie daje przedstawienie danych w postaci map. Wykonałam mapy dotyczące liczy aktualnych wykrytych przypadków, przypadków wyleczenia jak również przypadków śmierci związanych z Koronawirusem.
Stworzenie takiej mapy odbywa się za pomocą funkcji:
```
createMap(raw_data,colors,scope,title)
``` 

### Polska a inne kraje

Postanowiłam porównać sytuacje dla polski z dowolnym innym krajem dotkniętym problemem Koronawirusa. Całe porównanie zawarłam w jednej funkcji aby maksymalnie ułatwić wizualizację. Funkcja `comparePLwith(country,raw_data)` odpowiada za stworzenie DataFrame który można łatwo zwizualizować poleceniem plot(). Kraje do porównania z Polską wybrałam na podstawie wcześniejszej analizy danych na mapach i są to:

- **Chiny** – ze względu na dominującą przewagę w ilości wyzdrowiałych przypadków
- **Włochy** – ze względu na dominującą przewagę w każdym z analizowanych przypadków
- **USA** – ze względu na dominującą pozycję pod względem potwierdzonych przypadków
- **Niemcy** – ze względu na bezpośrednie sąsiedztwo z Polską, dużą ilość potwierdzonych jak również wyzdrowiałych przypadków i bardzo małą ilość śmierci.
- **Czechy** – ze względu na podobną sytuację i bezpośrednie sąsiedztwo z naszym Krajem
