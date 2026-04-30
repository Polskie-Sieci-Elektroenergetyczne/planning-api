# **Harmonogram dyspozycyjności**

## Informacja o harmonogramie dyspozycyjności dla zasobu w zadanym okresie
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca komunikatu | OSP (Operator Systemu Przesyłowego) |
| Odbiorca komunikatu | OSDp (Operator Systemu Dystrybucyjnego) |

### Charakterystyka komunikatu
Informacja o harmonogramie dyspozycyjności dla zasobu w zadanym okresie przekazuje dane planistyczne dotyczące zgłoszonego i przyjętego harmonogramu dyspozycyjności, w ramach horyzontu 5 lat (60 miesięcy). 

Harmonogram dyspozycyjności dotyczy całego zasobu, natomiast w szczególnych przypadkach:
* MWE hybrydowych, w skład których wchodzą moduły parku energii (PPM), 
* MWE, w skład których wchodzi oprócz składowej wytwórczej również składowa magazynowa,
udostępniane są serie danych na składowe takich MWE zamiast na całe MWE. 

Udostępniana jest minimalna i maksymalna dyspozycyjność elektrowniana oraz minimalna i maksymalna dyspozycyjność sieciowa. 

W sekcji szczegółowej każdej z serii udostępniany jest jeden bądź więcej poziomów dyspozycyjności (jako wartości nieujemne), a dla każdej z nich czas początku obowiązywania tej wielkości. 

Informacje otrzymywane w tym komunikacie wynikają z planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

## Endpointy API
---
### GET `.../resources/{mainResourceMrid}/availabilities`
Pobranie harmonogramu dyspozycyjności zasobu w zadanym okresie.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `mainResourceMrid` | string | path | tak | mRID zasobu | `_d8736017-d25d-4952-a3cf-0fa83560e16f` |
| `start` | date-time | query | tak | Początek zakresu | `2024-03-12T02:00:00Z` |
| `end` | date-time | query | tak | Koniec zakresu | `2024-03-13T02:00:00Z` |

**operationId:** `listAvailabilities`  
**Tag:** Current Planning Data  

| Kod | Opis |
|-----|------|
| 200 | Harmonogram dyspozycyjności zasobu |
| 400 | Nieprawidłowe parametry |
| 404 | Brak danych |