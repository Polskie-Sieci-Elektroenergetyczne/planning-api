# **Polecenia ruchowe OSD**

## Zgłoszenie poleceń ruchowych OSD
Nadawca: OSDp

Odbiorca: OSP

### Charakterystyka komunikatu
Zgłoszenie poleceń ruchowych OSD zawiera dane planistyczne dotyczące wskazanego przez OSD zakresu generacji w horyzoncie 9 dni.

Polecenia ruchowe OSD są przewidziane dla MWE typu B i C, przyłączonych do sieci OSDp, oprócz tych, które aktywnie uczestniczącą na rynku bilansującym poprzez powiązanie z JG<sub>W1</sub>. Ponadto polecenia ruchowe OSD są przewidziane dla MEE przyłączonych do sieci OSDp.

Polecenia ruchowe OSD nie są zgłaszane w odniesieniu do MWE typu B, C i D, które aktywnie uczestniczącą na rynku bilansującym poprzez powiązanie z JG<sub>W1</sub>.

Komunikat umożliwia zgłaszającym przekazanie poziomu minimalnej i maksymalnej generacji wynikającej z zakresu określonego przez polecenia OSD w ramach jednego zgłoszenia. 

W sekcji szczegółowej zgłoszenia dla grafiku mocy maksymalnej i grafiku mocy minimalnej wprowadzone są sekwencyjnie odpowiednie wielkości (jako wartości nieujemne) na każdy OREB w zadanym horyzoncie, zgodnie z początkiem i zakończeniem okresu poleceń ruchowych OSD określonym na poziomie ogólnym. Dopuszczalne są wielkości "puste" oznaczające brak ograniczeń wynikających z poleceń OSD.

Dane dotyczące poleceń ruchowych OSD powinny być przekazywane w sposób kompletny, przynajmniej raz dziennie dla poszczególnych OREB okresu obejmującego 9 kolejnych dni kalendarzowych, przy czym dane dotyczące pierwszych 8 dni są aktualizacją uprzednio przekazanych danych.

Informacje otrzymywane w tym komunikacie stanowią podstawę tworzenia lub korygowania planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

### Status obsługi komunikatu
**Zgłoszenie przyjęte** - dane dotyczące wskazanego (ograniczonego) przez OSD zakresu generacji są zaktualizowane o dane ze zgłoszenia.

**Zgłoszenie odrzucone** - dane dotyczące wskazanego (ograniczonego) przez OSD zakresu generacji pozostają bez aktualizacji o dane ze zgłoszenia.