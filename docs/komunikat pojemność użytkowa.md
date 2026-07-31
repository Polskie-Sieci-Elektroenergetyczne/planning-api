# **Pojemność użytkowa**

## Informacja o pojemności użytkowej dla zasobu w zadanym okresie
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca komunikatu | OSP (Operator Systemu Przesyłowego) |
| Odbiorca komunikatu | OSDp (Operator Systemu Dystrybucyjnego), Właściciel obiektu przyłączonego do sieci OSP |

### Charakterystyka komunikatu
Informacja o pojemności użytkowej dla zasobu w zadanym okresie przekazuje dane planistyczne dotyczące zgłoszonej i przyjętej pojemności użytkowej, w ramach horyzontu 5 lat (60 miesięcy). 

Pojemność użytkowa dotyczy MEE.

Udostępniane są poziomy pojemności użytkowej - bezkierunkowo, jako wartości nieujemne. Dla każdego z nich podawany jest czas początku obowiązywania tego poziomu. 

Informacje otrzymywane w tym komunikacie wynikają z planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

## Endpointy API
---
### GET `.../resources/{mainResourceMrid}/storage-capacities`
Pobranie danych o pojemności użytkowej magazynu.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `mainResourceMrid` | string | path | tak | mRID magazynu | `_d8736017-d25d-4952-a3cf-0fa83560e16f` |
| `start` | date-time | query | tak | Początek zakresu | `2024-03-12T02:00:00Z` |
| `end` | date-time | query | tak | Koniec zakresu | `2024-03-13T02:00:00Z` |

**operationId:** `listStorageCapacities`  
**Tag:** Current Planning Data  

| Kod | Opis |
|-----|------|
| 200 | Dane pojemności użytkowej |
| 400 | Błędne parametry |
| 404 | Brak danych |