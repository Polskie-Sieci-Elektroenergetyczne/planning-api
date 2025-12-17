# **Postoje**

## Zgłoszenie postoju
Nadawca: OSDp, Właściciel

Odbiorca: OSP

### Charakterystyka komunikatu
Zgłoszenie postoju zawiera dane planistyczne dotyczące całkowitej niedyspozycyjności zasobu w horyzoncie 5 lat (60 miesięcy). 

Postój jest dopuszczalny dla MWE typu D przyłączonych do sieci OSD lub OSP oraz MEE przyłączonych do sieci OSP.

W odniesieniu do MWE hybrydowych, w skład których wchodzą moduły parku energii (PPM) postoje mogą być zgłaszane na poszczególne składowe z danej kategorii źródła energii pierwotnej. Nie wyklucza to jednocześnie zgłoszenia w tym samym czasie postoju na całe MWE - taki postój będzie miał pierwszeństwo względem postoju na składowe.

Komunikat pozwala zgłaszać nowy postój albo modyfikować bądź wycofywać już zgłoszony postój. W zależności od kwalifikacji postoju i od czasu przekazania, odbiorcami zgłoszenia są pracownicy działu planowania lub dyspozytorzy OSP.

Komunikat zawiera informacje o kierunku, przyczynie oraz planowanych lub rzeczywistych datach początku i końca postoju. W przypadku MWE wytwórczych jako kierunek dopuszczalny jest jedynie postój całkowity.

Ponadto komunikat pozwala na przekazanie informacji o zdolności odzyskania dyspozycyjności w związku z przewidywaną przez zgłaszającego możliwością odwołania postoju. W dokumencie wskazuje się jedynie na potencjalną zdolność odzyskania dyspozycyjności i ma to charakter wyłącznie informacyjny.

Jeśli zasób jest powiązany z JG w sposób mapowalny, tzn. w skład JG wchodzi tylko ten zasób, to zgłoszony postój na zasób jednocześnie dotyczy tej powiązanej JG. Poza tym w odniesieniu do zasobu powiązanego z JG, gdzie ZAK=1, dopuszczalne jest przekazywanie informacji tylko o czasie rzeczywistego rozpoczęcia postoju - nie przekazuje się tym komunikatem daty zakończenia. Rzeczywista data i czas zakończenia postoju jest uzupełniana w ramach powiązanej JG w sposób automatyczny, na podstawie odpowiednich zdarzeń ruchowych dotyczących tej JG.

Pojedynczy dokument może dotyczyć postoju tylko w jednym kierunku.

W przypadku postoju już rozpoczętego dla zasobu powiązanego z JG<sub>W1</sub> opcjonalnie jest możliwe zgłoszenie charakterystyki uruchomienia dodatkowego, następującego po zgłaszanym postoju.

Informacje otrzymywane w tym komunikacie stanowią podstawę tworzenia lub korygowania planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

### Status obsługi komunikatu
**Zgłoszenie przyjęte** - postój zasobu jest zapisany w planie niedostępności w postaci zaktualizowanej o dane ze zgłoszenia.

**Zgłoszenie odrzucone** - postój zasobu nie jest zapisany w planie niedostępności w postaci zaktualizowanej o dane ze zgłoszenia.
