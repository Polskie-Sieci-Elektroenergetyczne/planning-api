 # **Saldo wymiany**

## Informacja o saldzie wymiany dla linii wymiany w zadanym okresie
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca komunikatu | OSP (Operator Systemu Przesyłowego) |
| Odbiorca komunikatu | OSDp (Operator Systemu Dystrybucyjnego) |

### Charakterystyka komunikatu
Informacja o saldzie wymiany dla linii wymiany nierównoległej w zadanym okresie przekazuje dane planistyczne dotyczące zgłoszonego i przyjętego salda wymiany nierównoległej realizowanej poprzez sieć 110 kV na wskazanej linii wymiany, w ramach horyzontu 5 lat (60 miesięcy). 

Udostępniane są wartości salda wymiany nierównoległej realizowanej poprzez sieć 110 kV na wskazanej linii wymiany. 

W sekcji szczegółowej udostępniany jest grafik salda wymiany, tj. sekwencyjna seria wielkości salda w zadanej rozdzielczości i horyzoncie.

Informacje otrzymywane w tym komunikacie wynikają z planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

## Endpointy API
---
### GET `.../resources/{mainResourceMrid}/exchange-schedules`
Pobranie planów wymiany.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `mainResourceMrid` | string | path | tak | mRID zasobu | `_d8736017-d25d-4952-a3cf-0fa83560e16f` |
| `start` | date-time | query | tak | Początek zakresu | `2024-03-12T02:00:00Z` |
| `end` | date-time | query | tak | Koniec zakresu | `2024-03-13T02:00:00Z` |

**operationId:** `listExchangeSchedules`  
**Tag:** Current Planning Data  

| Kod | Opis |
|-----|------|
| 200 | Plany wymiany |
| 400 | Nieprawidłowe parametry |
| 404 | Brak danych |
