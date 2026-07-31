# **Pojemność użytkowa**

## Zgłoszenie pojemności użytkowej
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca zgłoszenia | OSDp (Operator Systemu Dystrybucyjnego), Właściciel obiektu przyłączonego do sieci OSP |
| Odbiorca zgłoszenia | OSP (Operator Systemu Przesyłowego) |

### Charakterystyka komunikatu
Zgłoszenie danych o pojemności użytkowej zawiera dane planistyczne dotyczące poziomu pojemności użytkowej MEE w horyzoncie 5 lat (60 miesięcy).

Pojemność użytkowa jest przewidziana dla MEE przyłączonych do sieci OSDp oraz sieci OSP.

Komunikat umożliwia zgłaszającym przekazanie poziomów pojemności użytkowej (bezkierunkowo) w postaci harmonogramu, w ramach jednego zgłoszenia.

W sekcji szczegółowej zgłoszenia dla serii danych dotyczącej pojemności użytkowej wprowadzony jest jeden bądź więcej poziomów (jako wartości nieujemne), a dla każdego z nich czas początku obowiązywania tej wielkości. Czas rozpoczęcia pierwszego poziomu powinien być równy początkowi określonemu w części ogólnej zgłoszenia. Czas zakończenia podokresu dla ostatniego poziomu jest określony przez termin zakończenia pojemności użytkowej na poziomie ogólnym.

Dane dotyczące pojemności użytkowej powinny być przekazywane w sposób kompletny, nie później niż do 20. dnia każdego miesiąca, na okres kolejnych 60 miesięcy.

Informacje otrzymywane w tym komunikacie stanowią podstawę tworzenia lub korygowania planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

## Endpointy API

---

### POST `.../storage-capacity-submissions`
Przesłanie danych o zmianach pojemności użytkowej magazynów.

| Parametr | Typ | Lokalizacja | Wymagany | Opis |
|----------|-----|-------------|:--------:|------|
| — | — | body | tak | Obiekt `StorageCapacitySubmission` |

**operationId:** `submitStorageCapacity`  
**Tag:** Planning Data Submissions  

| Kod | Opis |
|-----|------|
| 202 | Przyjęto zgłoszenie do przetworzenia |
| 400 | Błędne dane wejściowe |

### Status obsługi komunikatu

| Status | Opis |
|--------|------|
| Komunikat przyjęty | Pojemność użytkowa jest zaktualizowana o dane ze zgłoszenia. |
| Komunikat odrzucony | Pojemność użytkowa pozostaje bez aktualizacji o dane ze zgłoszenia. |
	