# **Plany pracy**

## Zgłoszenie planu pracy
Nadawca: OSDp, Właściciel

Odbiorca: OSP

### Charakterystyka komunikatu
Zgłoszenie planu pracy zawiera dane planistyczne dotyczące generacji i ew. poboru zasobu w horyzoncie 9 dni. 

Plan pracy jest dopuszczalny dla MWE typu B, C i D przyłączonych do sieci OSD, MWE typu D przyłączonych do sieci OSP, MEE przyłączonych do sieci OSD lub OSP oraz pomp przyłączonych do sieci OSD lub OSP. 

W odniesieniu do MWE hybrydowych, w skład których wchodzą moduły parku energii (PPM), niektóre serie (grafiki) danych mają być zgłaszane dodatkowo na poszczególne składowe z danej kategorii źródła energii pierwotnej (jak podano powyżej). 

Plan pracy nie jest zgłaszany w odniesieniu do MWE typu B, C i D, które aktywnie uczestniczą na rynku bilansującym poprzez powiązanie z JG<sub>W1</sub>.

Komunikat umożliwia zgłaszającym przekazanie:

* **średniej** wielkości mocy wprowadzanej do sieci/pobieranej z sieci w ramach poszczególnych OREB,
* wielkości mocy wprowadzanej do sieci/pobieranej z sieci **na koniec** poszczególnych OREB,
* **średniej** wielkości mocy wprowadzanej do sieci/pobieranej z sieci w ramach poszczególnych OREB z uwzględnieniem polecenia ruchowego OSD,
* wielkości mocy wprowadzanej do sieci/pobieranej z sieci **na koniec** poszczególnych OREB z uwzględnieniem polecenia ruchowego OSD,

Dodatkowo dla MWE typu B, C, D, dane w kierunku generacji:

* **średniej** generacji mocy czynnej netto w ramach poszczególnych OREB na własne potrzeby (**autogeneracja**),
* generacji mocy czynnej netto **na koniec** poszczególnych OREB na własne potrzeby (**autogeneracja**),
* znacznika odzwierciedlania generacji mocy czynnej netto odpowiadającej potencjałowi generacji MWE wynikającemu z warunków meteorologicznych w poszczególnych OREB,
* znacznika odzwierciedlania generacji mocy czynnej netto odpowiadającej potencjałowi generacji MWE wynikającemu z warunków meteorologicznych na koniec  poszczególnych OREB,
* poziomu planowanej pracy wymuszonej (w kierunku generacji),

Dodatkowo dla PPM (w kategorii FW, PV lub układ hybrydowy), w tym dla poszczególnych elementów tego układu, dane w kierunku generacji:

* **średniej** generacji mocy czynnej netto w ramach poszczególnych OREB określających potencjał generacji MWE wynikający z warunków meteorologicznych i z **mocy dyspozycyjnej elektrownianej** MWE,
* generacji mocy czynnej netto **na koniec** poszczególnych OREB określających potencjał generacji MWE wynikający z warunków meteorologicznych i z **mocy dyspozycyjnej elektrownianej** MWE,
* **średniej** generacji mocy czynnej netto w ramach poszczególnych OREB określających potencjał generacji MWE wynikający z warunków meteorologicznych i z **mocy zainstalowanej** MWE,
* generacji mocy czynnej netto **na koniec** poszczególnych OREB określających potencjał generacji MWE wynikający z warunków meteorologicznych i z **mocy zainstalowanej** MWE.

W sekcji szczegółowej zgłoszenia dla każdego grafiku wprowadzone są sekwencyjnie odpowiednie wielkości (jako wartości nieujemne) na każdy OREB w zadanym horyzoncie, zgodnie z początkiem i zakończeniem planu pracy określonym na poziomie ogólnym.

Dane dotyczące planu pracy zasobu powinny być przekazywane w sposób kompletny, przynajmniej raz dziennie dla poszczególnych OREB okresu obejmującego 9 kolejnych dni kalendarzowych, przy czym dane dotyczące pierwszych 8 dni są aktualizacją uprzednio przekazanych danych.

W przypadku MWE wytwórczych dopuszczalne są jedynie serie danych w kierunku generacji. W odniesieniu do znacznika zgodności z prognozą, autogeneracji oraz pracy wymuszonej dopuszczalne są jedynie serie danych w kierunku generacji.

Informacje otrzymywane w tym komunikacie stanowią podstawę tworzenia lub korygowania planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

### Status obsługi komunikatu
**Zgłoszenie przyjęte** - dane o pracy zasobu są zaktualizowane o dane ze zgłoszenia.

**Zgłoszenie odrzucone** - dane o pracy zasobu pozostają bez aktualizacji o dane ze zgłoszenia.