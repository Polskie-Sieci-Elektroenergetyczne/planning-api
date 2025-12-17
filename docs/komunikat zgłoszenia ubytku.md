# **Ubytki**

## Zgłoszenie ubytku
Nadawca: OSDp, Właściciel

Odbiorca: OSP

### Charakterystyka komunikatu
Zgłoszenie ubytku zawiera dane planistyczne dotyczące częściowej niedyspozycyjności zasobu w horyzoncie 5 lat (60 miesięcy). 

Ubytek jest dopuszczalny dla MWE typu D przyłączonych do sieci OSD lub OSP oraz MEE przyłączonych do sieci OSP. 

W odniesieniu do MWE hybrydowych, w skład których wchodzą moduły parku energii (PPM) ubytki mogą być zgłaszane na poszczególne składowe z danej kategorii źródła energii pierwotnej. Nie wyklucza to jednocześnie zgłoszenia w tym samym czasie ubytku na całe MWE - taki ubytku będzie miał pierwszeństwo względem ubytku na składowe.

Komunikat pozwala zgłaszać nowy ubytek albo modyfikować bądź wycofywać już zgłoszony ubytek. W zależności od kwalifikacji ubytku i od czasu przekazania, odbiorcami zgłoszenia są pracownicy działu planowania lub dyspozytorzy OSP.

Komunikat umożliwia zgłaszającym przekazanie jednej lub więcej wielkości ubytku w danym okresie, w ramach jednego zgłoszenia. Oprócz tego zawiera informacje o rodzaju ubytku (dodatni lub ujemny), kierunku, przyczynie oraz planowanych lub rzeczywistych datach początku i końca ubytku. W przypadku MWE wytwórczych jako kierunek dopuszczalna jest jedynie generacja.

W sekcji szczegółowej zgłoszenia wprowadzona jest jedna bądź więcej wielkości ubytku (jako wartości nieujemne), a dla każdej z nich czas początku obowiązywania tej wielkości. Czas rozpoczęcia pierwszej z nich powinien być równy początkowi określonemu w części ogólnej zgłoszenia. Czas zakończenia podokresu dla ostatniej wielkości ubytku jest określony przez termin zakończenia ubytku na poziomie ogólnym.

Ponadto komunikat pozwala na przekazanie informacji o zdolności odzyskania dyspozycyjności w związku z przewidywaną przez zgłaszającego możliwością odwołania ubytku. W dokumencie wskazuje się jedynie na potencjalną zdolność odzyskania dyspozycyjności i ma to charakter wyłącznie informacyjny.

Pojedynczy dokument może dotyczyć ubytku tylko w jednym kierunku.

Dla danego zasobu i w danym kierunku można wprowadzić maksymalnie dwa ubytki, które nakładają się w czasie: jeden dodatni i jeden ujemny. Ubytki dodatnie obniżają dyspozycyjność zasobu, natomiast ubytki ujemne podwyższają jego moc minimalną. Pojedynczy dokument może dotyczyć ubytku tylko jednego rodzaju i w jednym kierunku.

Jeśli zasób jest powiązany z JG w sposób mapowalny, tzn. w skład JG wchodzi tylko ten zasób, to zgłoszony ubytek na zasób jednocześnie dotyczy tej powiązanej JG. 

Informacje otrzymywane w tym komunikacie stanowią podstawę tworzenia lub korygowania planów koordynacyjnych oraz ewidencjonowania stanów zasobów.

### Status obsługi komunikatu
**Zgłoszenie przyjęte** - ubytek dyspozycyjności zasobu jest zapisany w planie niedostępności w postaci zaktualizowanej o dane ze zgłoszenia.

**Zgłoszenie odrzucone** - ubytek dyspozycyjności zasobu nie jest zapisany w planie niedostępności w postaci zaktualizowanej o dane ze zgłoszenia.
