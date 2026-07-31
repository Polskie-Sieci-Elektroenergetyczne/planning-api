# **Plan niesprawności układów regulacji**

## Informacja o niesprawnościach układów regulacji dla zasobu w zadanym okresie
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca komunikatu | OSP (Operator Systemu Przesyłowego) |
| Odbiorca komunikatu | OSDp (Operator Systemu Dystrybucyjnego), Właściciel obiektu przyłączonego do sieci OSP |

### Charakterystyka komunikatu
Informacja o niesprawnościach układów regulacji dla zasobu w zadanym okresie przekazuje dane planistyczne dotyczące zgłoszonych i przyjętych do planu niesprawności układów regulacji zazębiających się z podanym okresem, w ramach horyzontu 5 lat (60 miesięcy). 

Mogą to być niesprawności układów regulacji na całe zasoby oraz, w odniesieniu do MWE hybrydowych, niesprawności na składowe wytwórcze takich MWE.

Komunikat zawiera informacje o parametrach niesprawności układów regulacji - rodzaju układu, kierunku lub jego braku oraz planowanych lub rzeczywistych datach początku i końca niesprawności. 

Komunikat może zawierać w sobie wiele niesprawności układów regulacji. 

Informacje otrzymywane w tym komunikacie wynikają z planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

## Endpointy API
---
### GET `.../resources/{mainResourceMrid}/control-malfunctions`
Pobranie listy niesprawności układów regulacji.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `mainResourceMrid` | string | path | tak | mRID zasobu | `_d8736017-d25d-4952-a3cf-0fa83560e16f` |
| `start` | date-time | query | tak | Początek zakresu | `2024-03-12T02:00:00Z` |
| `end` | date-time | query | tak | Koniec zakresu | `2024-03-13T02:00:00Z` |

**operationId:** `listControlMalfunctions`  
**Tag:** Current Planning Data  

| Kod | Opis |
|-----|------|
| 200 | Lista niesprawności układów regulacji |
| 400 | Błędne parametry |
| 404 | Brak danych |

---
### Charakterystyka komunikatu
Informacja o szczegółach wskazanej niesprawności układu regulacji dla zasobu przekazuje dane planistyczne dotyczące wybranej niesprawności układu regulacji, zgłoszonej i przyjętej do planu niesprawności. 

Komunikat zawiera informacje o parametrach wskazanej niesprawności układu regulacji - rodzaju układu, kierunku lub jego braku oraz planowanych lub rzeczywistych datach początku i końca niesprawności. 

Komunikat dotyczy tylko wskazanej niesprawności układu regulacji. 

Informacje otrzymywane w tym komunikacie wynikają z planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

### GET `.../resources/{mainResourceMrid}/control-malfunctions/{unavailabilityMrid}`
Pobranie szczegółów niesprawności układu regulacji.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `mainResourceMrid` | string | path | tak | mRID zasobu | `_d8736017-d25d-4952-a3cf-0fa83560e16f` |
| `unavailabilityMrid` | string | path | tak | mRID niesprawności | `12346017-d25d-4952-a3cf-0fa83560e160`` |

**operationId:** `getControlMalfunction`  
**Tag:** Current Planning Data  

| Kod | Opis |
|-----|------|
| 200 | Szczegóły niesprawności układu regulacji |
| 404 | Nie znaleziono |