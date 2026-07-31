# **Plan niedostępności - ubytki**

## Informacja o ubytkach dla zasobu w zadanym okresie
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca komunikatu | OSP (Operator Systemu Przesyłowego) |
| Odbiorca komunikatu | OSDp (Operator Systemu Dystrybucyjnego), Właściciel obiektu przyłączonego do sieci OSP |

### Charakterystyka komunikatu
Informacja o ubytkach dla zasobu w zadanym okresie przekazuje dane planistyczne dotyczące zgłoszonych i przyjętych do planu niedostępności ubytkach (częściowych niedyspozycyjności zasobu) zazębiających się z podanym okresem, w ramach horyzontu 5 lat (60 miesięcy). 

Ubytki mogą dotyczyć całych zasobów, a jeśli są to MWE posiadające wiele składowych (w szczególności MWE hybrydowych, w skład których wchodzą moduły parku energii, tj.PPM), to również składowych tych MWE.

Komunikat zawiera informacje o parametrach ubytków - rodzaju, kierunku, przyczynie, zdolności odzyskania dyspozycyjności oraz planowanych lub rzeczywistych datach początku i końca ubytku. Ponadto przekazywane są wielkości ubytku w ramach każdego z zazębiających się ubytków.

Komunikat może zawierać w sobie wiele ubytków. 

Informacje otrzymywane w tym komunikacie wynikają z planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

## Endpointy API
---
### GET `.../resources/{mainResourceMrid}/derates`
Pobranie listy ubytków zasobu.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `mainResourceMrid` | string | path | tak | mRID zasobu | `_d8736017-d25d-4952-a3cf-0fa83560e16f` |
| `start` | date-time | query | tak | Początek zakresu | `2024-03-12T02:00:00Z` |
| `end` | date-time | query | tak | Koniec zakresu | `2024-03-13T02:00:00Z` |

**operationId:** `listDerates`  
**Tag:** Current Planning Data  

| Kod | Opis |
|-----|------|
| 200 | Lista ubytków |
| 400 | Błędne parametry |
| 404 | Brak danych |

---
### Charakterystyka komunikatu
Informacja o szczegółach wskazanego ubytku dla zasobu przekazuje dane planistyczne dotyczące wybranego ubytku, zgłoszonego i przyjętego do planu niedostępności. 

Komunikat zawiera informacje o parametrach wskazanego ubytku - rodzaju, kierunku, przyczynie, zdolności odzyskania dyspozycyjności oraz planowanych lub rzeczywistych datach początku i końca ubytku. Ponadto przekazywa jest wielkość tego ubytku, ew. zmieniająca się w podokresach.

Komunikat dotyczy tylko wskazanego ubytku. 

Informacje otrzymywane w tym komunikacie wynikają z planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

### GET `.../resources/{mainResourceMrid}/derates/{unavailabilityMrid}`
Pobranie szczegółów ubytku.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `mainResourceMrid` | string | path | tak | mRID zasobu | `_d8736017-d25d-4952-a3cf-0fa83560e16f` |
| `unavailabilityMrid` | string | path | tak | mRID ubytku | `12346017-d25d-4952-a3cf-0fa83560e160`` |

**operationId:** `getDerate`  
**Tag:** Current Planning Data  

| Kod | Opis |
|-----|------|
| 200 | Szczegóły ubytku |
| 404 | Nie znaleziono |