# **Ograniczenia zdolności regulacji mocy biernej**

## Zgłoszenie ograniczenia zdolności regulacji mocy biernej
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca zgłoszenia | OSDp (Operator Systemu Dystrybucyjnego), Właściciel obiektu przyłączonego do sieci OSP |
| Odbiorca zgłoszenia | OSP (Operator Systemu Przesyłowego) |

### Charakterystyka komunikatu
Zgłoszenie jest przekazywane w sytuacji planowanego bądź awaryjnego ograniczenia zdolności regulacji mocy biernej. Całkowity brak zdolności regulacji mocy biernej należy zgłaszać odrębnym komunikatem: [Niesprawności układu regulacji](komunikat%20zgłoszenia%20niesprawności.md)

Zgłoszenie zawiera dane planistyczne dotyczące poziomów dyspozycyjności minimalnej i maksymalnej zakresu regulacji mocy biernej danego rodzaju mocy (indukcyjna, pojemnościowa) dla wskazanego stanu zasobu/składowej zasobu.

Zgłoszenie ograniczenia zdolności regulacji mocy biernej jest dopuszczalne dla MWE typu D przyłączonych do sieci OSD lub OSP oraz MEE przyłączonych do sieci OSP.

W odniesieniu do MWE, w skład których wchodzi więcej niż jedna kategoria źródła energii pierwotnej (MWE typu układ hybrydowy), dane należy zgłaszać dla poszczególnych składowych odpowiadających kategoriom źródeł energii pierwotnej tego MWE.

W sekcji szczegółowej zgłoszenia dla każdej serii danych wprowadzony jest jeden bądź więcej poziomów dyspozycyjności (jako wartości nieujemne), a dla każdej z nich czas początku obowiązywania tej wielkości. Czas rozpoczęcia pierwszego poziomu powinien być równy początkowi określonemu w części ogólnej zgłoszenia. Czas zakończenia podokresu dla ostatniego poziomu jest określony przez termin zakończenia harmonogramu na poziomie ogólnym.

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