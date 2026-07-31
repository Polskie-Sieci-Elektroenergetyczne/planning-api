# **Saldo wymiany**

## Zgłoszenie salda wymiany
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca zgłoszenia | OSDp (Operator Systemu Dystrybucyjnego) |
| Odbiorca zgłoszenia | OSP (Operator Systemu Przesyłowego) |

### Charakterystyka komunikatu
Zgłoszenie grafiku z saldem wymiany zawiera dane planistyczne dotyczące salda wymiany nierównoległej realizowanej poprzez sieć 110 kV na wskazanej linii wymiany, w całkowitym horyzoncie planowania 5 lat (60 miesięcy).

Saldo wymiany jest przewidziane dla linii wymiany nierównoległej.

Komunikat umożliwia zgłaszającym przekazanie wartości salda wymiany dla danej linii wymiany w ramach jednego zgłoszenia. 

W sekcji szczegółowej zgłoszenia dla grafiku salda wymiany wprowadzone są sekwencyjnie odpowiednie wielkości (jako wartości nieujemne) w zadanej rozdzielczości i horyzoncie, zgodnie z początkiem i zakończeniem okresu określonym na poziomie ogólnym.

Dane dotyczące salda wymiany nierównoległej powinny być przekazywane w sposób kompletny, nie później niż do 20. dnia każdego miesiąca, na okres kolejnych 60 miesięcy, przy czym:

* dla horyzontu planowania 9 dób naprzód dane należy przekazywać w rozdzielczości godzinowej,
* dla horyzontu planowania 1 roku naprzód dane należy przekazywać w rozdzielczości dobowej (dla szczytów obciążenia każdej doby),
* dla horyzontu planowania 5 lat dane należy przekazywać w rozdzielczości miesięcznej (wartości średniomiesięczne w okresach szczytów dobowych dni roboczych).

Informacje otrzymywane w tym komunikacie stanowią podstawę tworzenia lub korygowania planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

## Endpointy API

---

### POST `.../exchange-schedule-submissions`
Przesłanie planu wymiany 110kV.

| Parametr | Typ | Lokalizacja | Wymagany | Opis |
|----------|-----|-------------|:--------:|------|
| — | — | body | tak | Obiekt `ExchangeScheduleSubmission` |

**operationId:** `submitExchangeSchedule`  
**Tag:** Planning Data Submissions  

| Kod | Opis |
|-----|------|
| 202 | Przyjęto zgłoszenie do przetworzenia |
| 400 | Niepoprawne zgłoszenie |

### Status obsługi komunikatu

| Status | Opis |
|--------|------|
| Komunikat przyjęty | Wartości salda wymiany są zaktualizowane o dane ze zgłoszenia. |
| Komunikat odrzucony | Wartości salda wymiany nie są zaktualizowane o dane ze zgłoszenia. |