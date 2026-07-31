# **Polecenia ruchowe OSD**

## Informacja o poleceniach ruchowych OSD dla zasobu w zadanym okresie
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca komunikatu | OSP (Operator Systemu Przesyłowego) |
| Odbiorca komunikatu | OSDp (Operator Systemu Dystrybucyjnego) |

### Charakterystyka komunikatu
Informacja o poleceniach ruchowych OSD dla zasobu w zadanym okresie przekazuje dane planistyczne dotyczące wskazanego przez OSD zakresu generacji. 

Udostępniane są poziomy minimalnej i mocy w danym (dostępnym) kierunku wynikającej z zakresu określonego przez polecenia OSD. 

W sekcji szczegółowej zgłoszenia udostępniane są sekwencyjnie odpowiednie wielkości (jako wartości nieujemne lub wartości puste) na każdy OREB w zadanym horyzoncie, zgodnie z początkiem i zakończeniem okresu poleceń ruchowych OSD określonym na poziomie ogólnym.

Informacje otrzymywane w tym komunikacie wynikają z planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

## Endpointy API
---
### GET `.../resources/{mainResourceMrid}/dispatch-instructions`
Pobranie poleceń ruchowych OSD.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `mainResourceMrid` | string | path | tak | mRID zasobu | `_d8736017-d25d-4952-a3cf-0fa83560e16f` |
| `start` | date-time | query | tak | Początek zakresu | `2024-03-12T02:00:00Z` |
| `end` | date-time | query | tak | Koniec zakresu | `2024-03-13T02:00:00Z` |

**operationId:** `listDispatchInstructions`  
**Tag:** Current Planning Data  

| Kod | Opis |
|-----|------|
| 200 | Polecenia ruchowe OSD |
| 400 | Błędne parametry |
| 404 | Brak danych |