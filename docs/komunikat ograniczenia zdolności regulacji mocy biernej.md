# **Ograniczenia zdolności regulacji mocy biernej**

## Informacja o ograniczeniach zdolności regulacji mocy biernej dla zasobu w zadanym okresie
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca komunikatu | OSP (Operator Systemu Przesyłowego) |
| Odbiorca komunikatu | OSDp (Operator Systemu Dystrybucyjnego), Właściciel obiektu przyłączonego do sieci OSP |

### Charakterystyka komunikatu
Informacja o ograniczeniach zdolności regulacji mocy biernej dla zasobu w zadanym okresie przekazuje dane planistyczne dotyczące zgłoszonych zakresów regulacji mocy biernej. 

Mogą to być ograniczenia zdolności regulacji mocy biernej na całe zasoby oraz, w odniesieniu do MWE hybrydowych, ograniczenia na składowe wytwórcze takich MWE.

Komunikat udostępnia tylko dane ograniczeń przekazane komunikatem: Zgłoszenie ograniczenia zdolności regulacji mocy biernej (ORMB). Informacje o zgłoszonych całkowitych niesprawnościach układu regulacji pozyskać można poprzez komunikat: [Komunikat niesprawności](komunikat%20niesprawno%C5%9Bci.md?ref_type=heads).

Udostępniana jest minimalna i maksymalna dyspozycyjność układu regulacji mocy biernej danego rodzaju mocy dla wskazanego stanu zasobu (lub składowej zasobu). 

W sekcji szczegółowej każdej z serii udostępniany jest jeden bądź więcej poziomów dyspozycyjności (jako wartości nieujemne), a dla każdej z nich czas początku obowiązywania tej wielkości. 

## Endpointy API
---
### GET `.../resources/{mainResourceMrid}/reactive-limits`
Pobranie ograniczeń zdolności regulacji mocy biernej w zadanym okresie.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `mainResourceMrid` | string | path | tak | mRID zasobu | `_d8736017-d25d-4952-a3cf-0fa83560e16f` |
| `start` | date-time | query | tak | Początek zakresu (UTC) | `2024-03-12T02:00:00Z` |
| `end` | date-time | query | tak | Koniec zakresu (UTC) | `2024-03-13T02:00:00Z` |

**operationId:** `listReactiveLimits`  
**Tag:** Current Planning Data  