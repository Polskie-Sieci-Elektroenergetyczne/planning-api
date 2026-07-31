# **Niesprawności układu regulacji**

## Zgłoszenie niesprawności układu regulacji
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca zgłoszenia | OSDp (Operator Systemu Dystrybucyjnego), Właściciel obiektu przyłączonego do sieci OSP |
| Odbiorca zgłoszenia | OSP (Operator Systemu Przesyłowego) |

### Charakterystyka komunikatu
Zgłoszenie niesprawności układu regulacji zawiera dane planistyczne dotyczące niesprawności układu regulacji pierwotnej, wtórnej lub mocy biernej zasobu w horyzoncie 5 lat (60 miesięcy). 

Niesprawność układu regulacji w zakresie regulacji pierwotnej lub wtórnej oraz niesprawność układu regulacji mocy biernej jest przewidziana dla MWE typu D przyłączonych do sieci OSD lub OSP oraz MEE przyłączonych do sieci OSP.

W odniesieniu do MWE posiadających wiele składowych (w szczególności MWE hybrydowych, w skład których wchodzą moduły parku energii, tj.PPM), niesprawności oprócz zgłaszania na całe MWE mogą być zgłaszane również na poszczególne składowe wytwórcze z danej kategorii źródła energii pierwotnej. Pojedynczy komunikat odnosi się tylko do jednego obiektu (albo całego MWE albo jego składowej).

Komunikat pozwala zgłaszać nową niesprawność układu regulacji albo modyfikować bądź wycofywać już zgłoszoną niesprawność. W zależności od czasu przekazania, odbiorcami zgłoszenia są pracownicy działu planowania lub dyspozytorzy OSP.

Komunikat zawiera informacje o rodzaju układu regulacji, kierunku (ew. braku kierunku) oraz planowanych lub rzeczywistych datach początku i końca niesprawności tego układu regulacji. W przypadku MWE wytwórczych  dla regulacji pierwotnej lub wtórnej jako kierunek jest dopuszczalna generacja. Niesprawność układu regulacji w zakresie mocy biernej (ARNE) jest zawsze bezkierunkowa.

Informacje otrzymywane w tym komunikacie stanowią podstawę tworzenia lub korygowania planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

## Endpointy API

---

### POST `.../control-malfunction-submissions`
Zgłoszenie, modyfikacja lub wycofanie niesprawności układu regulacji.

| Parametr | Typ | Lokalizacja | Wymagany | Opis |
|----------|-----|-------------|:--------:|------|
| — | — | body | tak | Obiekt `ControlMalfunctionSubmission` |

**operationId:** `submitControlMalfunction`  
**Tag:** Planning Data Submissions  

| Kod | Opis |
|-----|------|
| 202 | Przyjęto zgłoszenie do przetworzenia |
| 400 | Błędny format zgłoszenia |

### Status obsługi komunikatu

| Status | Opis |
|--------|------|
| Komunikat przyjęty | Niesprawność układu regulacji zasobu jest zapisana w planie niesprawności w postaci zaktualizowanej o dane ze zgłoszenia. |
| Komunikat odrzucony | Niesprawność układu regulacji zasobu nie jest zapisana w planie niesprawności w postaci zaktualizowanej o dane ze zgłoszenia. |