# **Plan niedostępności - postoje**

## Informacja o postojach dla zasobu w zadanym okresie
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca komunikatu | OSP (Operator Systemu Przesyłowego) |
| Odbiorca komunikatu | OSDp (Operator Systemu Dystrybucyjnego), Właściciel obiektu przyłączonego do sieci OSP |

### Charakterystyka komunikatu
Informacja o postojach dla zasobu w zadanym okresie przekazuje dane planistyczne dotyczące zgłoszonych i przyjętych do planu niedostępności postojów (całkowitych niedyspozycyjności zasobu) zazębiających się z podanym okresem, w ramach horyzontu 5 lat (60 miesięcy). 

Mogą to być zarówno postoje na całe zasoby jak i, w odniesieniu do MWE hybrydowych, postoje na składowe takich MWE.

Komunikat zawiera informacje o parametrach postojów - kierunku, przyczynie, zdolności odzyskania dyspozycyjności oraz planowanych lub rzeczywistych datach początku i końca postoju. 

Komunikat może zawierać w sobie wiele postojów. 

Informacje otrzymywane w tym komunikacie wynikają z planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

## Endpointy API
---
### GET `.../resources/{mainResourceMrid}/outages`
Pobranie listy postojów zasobu.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `mainResourceMrid` | string | path | tak | mRID zasobu | `_d8736017-d25d-4952-a3cf-0fa83560e16f` |
| `start` | date-time | query | tak | Początek zakresu | `2024-03-12T02:00:00Z` |
| `end` | date-time | query | tak | Koniec zakresu | `2024-03-13T02:00:00Z` |

**operationId:** `listOutages`  
**Tag:** Current Planning Data  

| Kod | Opis |
|-----|------|
| 200 | Lista postojów |
| 400 | Błędne parametry |
| 404 | Brak danych |

---

### GET `.../resources/{mainResourceMrid}/outages/{unavailabilityMrid}`
Pobranie szczegółów postoju zasobu.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `mainResourceMrid` | string | path | tak | mRID zasobu | `_d8736017-d25d-4952-a3cf-0fa83560e16f` |
| `unavailabilityMrid` | string | path | tak | mRID awarii | `12346017-d25d-4952-a3cf-0fa83560e160` |

**operationId:** `getOutage`  
**Tag:** Current Planning Data  

| Kod | Opis |
|-----|------|
| 200 | Szczegóły postoju |
| 404 | Awaria nie istnieje |
