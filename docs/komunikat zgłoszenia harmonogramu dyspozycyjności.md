# **Harmonogramy dyspozycyjności**

## Zgłoszenie harmonogramu dyspozycyjności
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca zgłoszenia | OSDp (Operator Systemu Dystrybucyjnego) |
| Odbiorca zgłoszenia | OSP (Operator Systemu Przesyłowego) |

### Charakterystyka komunikatu
Zgłoszenie harmonogramu dyspozycyjności zawiera dane planistyczne dotyczące poziomów dyspozycyjności minimalnej i maksymalnej zasobu w horyzoncie 5 lat (60 miesięcy). 

Harmonogram dyspozycyjności jest przewidziany dla MWE typu B i C przyłączonych do sieci OSD oraz MEE przyłączonych do sieci OSD.  

W odniesieniu do MWE posiadających wiele składowych (w szczególności MWE hybrydowych, w skład których wchodzą moduły parku energii, tj.PPM), harmonogramy mają być zgłaszane na całość MWE oraz na poszczególne składowe: wytwórcze z danej kategorii źródła energii pierwotnej i  magazynową, jeśli występuje. 

Komunikat umożliwia zgłaszającym przekazanie minimalnej i maksymalnej dyspozycyjności elektrownianej oraz minimalnej i maksymalnej dyspozycyjności sieciowej w danym kierunku, w ramach jednego zgłoszenia. W przypadku MWE wytwórczych jako kierunek dopuszczalna jest jedynie generacja.

W sekcji szczegółowej zgłoszenia dla każdej serii danych wprowadzony jest jeden bądź więcej poziomów dyspozycyjności (jako wartości nieujemne), a dla każdej z nich czas początku obowiązywania tej wielkości. Czas rozpoczęcia pierwszego poziomu powinien być równy początkowi określonemu w części ogólnej zgłoszenia. Czas zakończenia podokresu dla ostatniego poziomu jest określony przez termin zakończenia harmonogramu na poziomie ogólnym.

Jeśli zasób jest powiązany z JG, to zgłoszony harmonogram dyspozycyjności na zasób nie wpływa na dyspozycyjność powiązanej JG (zasób nie jest powiązany w sposób mapowalny). 

Dane dotyczące dyspozycyjności zasobu powinny być przekazywane w sposób kompletny, nie później niż do 20. dnia każdego miesiąca, na okres kolejnych 60 miesięcy.

Informacje otrzymywane w tym komunikacie stanowią podstawę tworzenia lub korygowania planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

## Endpointy API

---

### POST `.../availability-submissions`
Przesłanie harmonogramu dyspozycyjności.

| Parametr | Typ | Lokalizacja | Wymagany | Opis |
|----------|-----|-------------|:--------:|------|
| — | — | body | tak | Obiekt `AvailabilitySubmission` |

**operationId:** `submitAvailability`  
**Tag:** Planning Data Submissions  

| Kod | Opis |
|-----|------|
| 202 | Zgłoszenie przyjęte |
| 400 | Błędne dane wejściowe |

### Status obsługi komunikatu

| Status | Opis |
|--------|------|
| Komunikat przyjęty | Dyspozycyjność zasobu jest zaktualizowana o dane ze zgłoszenia. |
| Komunikat odrzucony | Dyspozycyjność zasobu pozostaje bez aktualizacji o dane ze zgłoszenia. |