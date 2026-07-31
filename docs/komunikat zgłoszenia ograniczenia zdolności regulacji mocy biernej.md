# **Ograniczenia zdolności regulacji mocy biernej**

## Zgłoszenie ograniczenia zdolności regulacji mocy biernej
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca zgłoszenia | OSDp (Operator Systemu Dystrybucyjnego), Właściciel obiektu przyłączonego do sieci OSP |
| Odbiorca zgłoszenia | OSP (Operator Systemu Przesyłowego) |

### Charakterystyka komunikatu
Zgłoszenie ograniczenia zdolności regulacji mocy biernej zawiera dane planistyczne dotyczące poziomów dyspozycyjności minimalnej i maksymalnej zakresu regulacji mocy biernej danego rodzaju (indukcyjna, pojemnościowa) dla wskazanego stanu zasobu lub składowej zasobu, w horyzoncie 5 lat (60 miesięcy). Zgłoszenie jest przekazywane w sytuacji planowanego bądź awaryjnego ograniczenia zdolności regulacji mocy biernej. Całkowity brak zdolności regulacji mocy biernej należy zgłaszać odrębnym komunikatem: [Niesprawności układu regulacji](komunikat%20zgłoszenia%20niesprawności.md). Przyjęta niesprawność układu regulacji mocy biernej (ARNE), która nakłada się na okres ograniczenia, ma pierwszeństwo, tj. przykrywa zgłoszone ograniczenia zdolności regulacji mocy biernej.

Zgłoszenie ograniczenia zdolności regulacji mocy biernej jest przewidziane dla MWE typu D przyłączonych do sieci OSD lub OSP oraz MEE przyłączonych do sieci OSDp lub OSP.

W odniesieniu do MWE posiadających wiele składowych (w szczególności MWE hybrydowych, w skład których wchodzą moduły parku energii, tj.PPM), ograniczenia mają być zgłaszane na całość MWE oraz na poszczególne składowe wytwórcze z danej kategorii źródła energii pierwotnej.

Komunikat umożliwia zgłaszającym w ramach jednego zgłoszenia przekazanie wybranego zestawu danych: dyspozycyjności minimalnej i maksymalnej zakresu regulacji mocy biernej danego rodzaju (indukcyjna, pojemnościowa), w danym stanie zasobu (praca, kompensacja) oraz w danym kierunku pracy zasobu. Przy tym kierunek całkowity oznacza ograniczenie dostępności regulacji mocy biernej niezależnie od kierunku, w którym miałby pracować zasób.

W sekcji szczegółowej zgłoszenia dla każdej wybranej serii danych wprowadzony jest jeden bądź więcej poziomów dyspozycyjności (jako wartości nieujemne), a dla każdej z nich czas początku obowiązywania tej wielkości. Czas rozpoczęcia pierwszego poziomu powinien być równy początkowi określonemu w części ogólnej zgłoszenia. Czas zakończenia podokresu dla ostatniego poziomu jest określony przez termin zakończenia harmonogramu regulacji na poziomie ogólnym.

## Endpointy API

---


### POST `.../reactive-limit-submissions`
Przesłanie zgłoszenia ograniczeń zdolności regulacji mocy biernej.

| Parametr | Typ | Lokalizacja | Wymagany | Opis |
|----------|-----|-------------|:--------:|------|
| — | — | body | tak | Obiekt `ReactiveLimitSubmission` |

**operationId:** `submitReactiveLimit`  
**Tag:** Planning Data Submissions  

| Kod | Opis |
|-----|------|
| 202 | Zgłoszenie przyjęte do przetwarzania |
| 400 | Nieprawidłowy format lub struktura zgłoszenia |

### Status obsługi komunikatu

| Status | Opis |
|--------|------|
| Komunikat przyjęty | Dane dotyczące ograniczeń zdolności regulacji mocy biernej są zaktualizowane o dane ze zgłoszenia.|
| Komunikat odrzucony | Dane dotyczące ograniczeń zdolności regulacji mocy biernej pozostają bez aktualizacji o dane ze zgłoszenia. |