
# WYMIANA DANYCH PLANISTYCZNYCH 

Poniżej przedstawiono specyfikację zakresu i formatu danych planistycznych wymienianych przez dedykowany system informatyczny OSP (kanał B2B). Specyfikacja opiera się na dokumencie „Zakres wymienianych danych dla potrzeb planowania pracy i prowadzenia ruchu KSE” (TCM - zakres wymienianych danych, opracowany na podstawie art. 40 ust. 5 SO GL) oraz na IRiESP. Dane wymieniane są pomiędzy OSP, OSD i SGU (znaczących użytkowników sieci) w procesach związanych z zarządzaniem pracą KSE w zakresie niezbędnym do bilansowania mocy KSE. Dane te są przesyłane w postaci komunikatów elektronicznych o ściśle określonym formacie. 

Korzystanie z kanału wymiany danych B2B wymaga od uczestniczących w wymianie informacji z OSP zarejestrowania się jako partner biznesowy OSP 
i uzyskania identyfikatora partnera biznesowego.

## Dokumenty źródłowe
Niniejsze standardy w zakresie wymiany danych planistycznych opierają się na następujących dokumentach po ich ostatnich zmianach:
* Dokument TCM „Zakres wymienianych danych dla potrzeb planowania pracy i prowadzenia ruchu KSE” (opracowany na podstawie art. 40 ust. 5 SO GL) zatwierdzony przez Prezesa URE w dniu 22.04.2026.
* Instrukcja Ruchu i Eksploatacji Sieci Przesyłowej (IRiESP) ze zmianami wynikającymi z Karty aktualizacji nr 3/CK-3/2025 do IRiESP, zatwierdzonej przez Prezesa URE w dniu 19.06.2026.

Oprócz tego standardy odnoszą się do dokumentów:
* Warunki Dotyczące Bilansowania (WDB) z dnia 14 września 2023 roku
* Standardy techniczne systemu SOWE wersja 9.0

## Specyfikacja OpenAPI
Pełna specyfikacja techniczna API dostępna jest w pliku: [`specs/planning-openapi.yml`](specs/planning-openapi.yml)

> Log zmian znajduje się w [CHANGELOG.md](CHANGELOG.md)

Dostępna jest również [dokumentacja API w formacie REDOC](https://polskie-sieci-elektroenergetyczne.github.io/planning-api/)
| Parametr | Wartość |
|----------|---------|
| **Adres bazowy** | `https://b2b.pse.pl` |
| **Ścieżka bazowa** | `/pwdp/api/v1/` |
| **Uwierzytelnianie** | mTLS — certyfikaty klienckie X.509 podpisane przez zaufany CA operatora |
| **Format danych** | JSON |


## Oznaczenia
W poniższym opisie oraz tabeli zastosowano następujące nazwy i oznaczenia:
* Obiekt generacji lub poboru – ogólne określenie obiektu, na który zgłaszane są dane dotyczące planowanej generacji lub poboru, albo też dane dotyczące dyspozycyjności. Są to zasoby: MWE, MEE, pompy.
* Obiekt wymiany – obiekt, na który zgłaszane są dane dotyczące planowanej wymiany nierównoległej poprzez sieć 110 kV. Są to linie wymiany bądź grupy linii wymiany.
* Właściciel – Wytwórca lub inny podmiot należący do znaczących użytkowników sieci (SGU), który jest właścicielem obiektu generacji lub poboru. Właściciela może również zastępować jednoznacznie określony inny podmiot, który pełni rolę przedstawiciela tego SGU.
* ZWE - Zakład Wytwarzania Energii,
* ESP - Elektrownia Szczytowo-Pompowa,
* PPM - MWE typu moduł parku energii,
* IWM – MWE hybrydowy, posiadający również składową o kategorii magazyn (tj. instalację magazynowania energii elektrycznej przyłączoną w jednym miejscu sieci elektroenergetycznej poprzez układ energoelektroniki) dla źródła energii pierwotnej, która wspiera pracę instalacji wytwórczej
* OREB - okres rozliczania energii bilansującej (pojęcie zdefiniowane w WDB).
* ZAK – znacznik aktywności na rynku bilansującym (pojęcie zdefiniowane w WDB).

<br>

## Ogólne zestawienie przekazywanych danych planistycznych

###	Zakres obiektów
Zakres obiektów, których dotyczy pozyskiwanie danych planistycznych w związku z wyżej wymienionymi zmianami dokumentów źródłowych obejmuje zarówno zasoby wytwórcze jak i umożliwiające realizację zdolności magazynowana energii. Ponieważ bloki energetyczne ESP mogą składać się albo z hydrozespołów odwracalnych, albo z oddzielnych generatorów i pomp, zatem obiektami, na które pozyskuje się dane planistyczne, mogą być, odpowiednio do budowy bloków ESP: MWE lub pompy.

Pozyskiwanie danych planistycznych dotyczy obiektów:
* MWE (Moduły Wytwarzania Energii)
* Magazyny chemiczne MEE (Magazyn Energii Elektrycznej) – wyłącznie o mocy maksymalnej netto większej niż 50 kW
* Pompy – stanowiące część ZWE typu ESP
* Linie wymiany 

W ramach MWE mogą wystąpić MWE hybrydowe, tj. MWE, które są modułami parku energii (PPM): 
* posiadające jeden punkt przyłączenia do systemu przesyłowego lub systemu dystrybucyjnego,
* zawierające zestaw jednostek wytwarzających energię elektryczną z wykorzystaniem różnych źródeł energii pierwotnej, wykorzystujących do wytwarzania energii elektrycznej energię promieniowania słonecznego lub energię wiatru,
* posiadające technologię wytwarzania energii: Układ hybrydowy (źródła OZE o różnych technologiach wytwarzania)
* przyłączone do sieci w sposób niesynchroniczny lub poprzez układy energoelektroniki.

MWE hybrydowe mogą dodatkowo zawierać jednostkę umożliwiającą magazynowanie energii, która wspiera pracę instalacji wytwórczej, tworząc w ten sposób instalację wytwórczo-magazynową (IWM).

### Kanał komunikacji
Wymiana danych planistycznych odbywa się poprzez dedykowany kanał B2B, którym za pomocą zdefiniowanych komunikatów można zgłaszać dane odpowiednio do wymogów zawartych we wskazanych dokumentach źródłowych.
W ramach komunikacji kanałem B2B będzie zapewniona kontrola przesyłanych komunikatów ze zgłoszeniami w zakresie dopuszczalności ich przesyłania do Operatora Systemu Przesyłowego, poprawności struktury i formatu.

### Zakres danych planistycznych
Poniżej przedstawiono zakres danych planistycznych przekazywanych poprzez kanał B2B. Są to zarówno dane o charakterze grafikowym jak i dane okresowe, tj. niedyspozycyjności: postoje, ubytki i niesprawności układu regulacji. 

Zachowanie ciągłości informacji i jednokrotnego zgłaszania niedostępności (w odniesieniu do kanału SOWE) dotyczy jedynie zasóbów, gdzie jednostka grafikowa jest powiązana wyłącznie z tym zasobem (JG = zasób) oraz gdzie na ten zasób zgłasza się postoje i ubytki. W tej sytuacji zgłoszenie danych na zasób jednocześnie bezpośrednio dotyczy powiązanej JG. W przypadku powiązania wielu zasobów do jednej JG albo powiązania JG z jednym zasobem, w odniesieniu do którego zgłasza się harmonogramy dyspozycyjności, zgłoszenia na poszczególny zasób oraz na JG są traktowane niezależnie.

Dane planistyczne przekazywane są przez OSDp oraz poszczególnych właścicieli wypełniających obowiązki SOGL w porządku jak przedstawiono w poniższej tabeli. 

| Nadawca | Obiekt generacji lub poboru albo obiekt wymiany | Aktywność na rynku bilansującym | Rodzaj przekazywanych danych | 
|-----------| :---------: | :---------: |-----------|
|OSDp |	MWE typu B lub C w sieci OSDp	| Brak lub dowolny rodzaj JG poza JG<sub>W1</sub> | Harmonogram dyspozycyjności przekazywany przez OSDp dla horyzontu od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Plan pracy przekazywany dla horyzontu dobowego (od doby bieżącej do doby d+9) <br /><br /> Polecenia ruchowe OSD dla horyzontu dobowego (od doby bieżącej do doby d+9) |
|OSDp | MWE typu B lub C w sieci OSDp | JG<sub>W1</sub> | Harmonogram dyspozycyjności przekazywany przez OSDp dla horyzontu od doby bieżącej do 5 lat (60 miesięcy) naprzód |
| OSDp | MWE typu D w sieci OSDp | Brak lub dowolny rodzaj JG poza JG<sub>W1</sub> | Niedostępność (postój, ubytek dodatni, ubytek ujemny) dla horyzontu od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Niesprawność regulacji pierwotnej, wtórnej lub ARNE (w przypadku świadczenia usług) od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Plan pracy MWE przekazywany dla horyzontu dobowego (od doby bieżącej do doby d+9) <br /><br /> Ograniczenia zdolności regulacji mocy biernej od doby bieżącej do 5 lat (60 miesięcy) naprzód |
OSDp | MWE typu D w sieci OSDp | JG<sub>W1</sub> | Niedostępność (postój, ubytek dodatni, ubytek ujemny) dla horyzontu od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Niesprawność regulacji pierwotnej, wtórnej lub ARNE (w przypadku świadczenia usług) od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Ograniczenia zdolności regulacji mocy biernej od doby bieżącej do 5 lat (60 miesięcy) naprzód |
Właściciel | MWE typu D w sieci OSP | Brak lub dowolny rodzaj JG poza JG<sub>W1</sub> | Niedostępność (postój, ubytek dodatni, ubytek ujemny) dla horyzontu od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Niesprawność regulacji pierwotnej, wtórnej lub ARNE (w przypadku świadczenia usług) od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Plan pracy MWE przekazywany dla horyzontu dobowego (od doby bieżącej do doby d+9) <br /><br /> Ograniczenia zdolności regulacji mocy biernej od doby bieżącej do 5 lat (60 miesięcy) naprzód |
Właściciel | MWE typu D w sieci OSP | JG<sub>W1</sub> | Niedostępność (postój, ubytek dodatni, ubytek ujemny) dla horyzontu od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Niesprawność regulacji pierwotnej, wtórnej lub ARNE (w przypadku świadczenia usług) od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Ograniczenia zdolności regulacji mocy biernej od doby bieżącej do 5 lat (60 miesięcy) naprzód | |
| OSDp | MEE w sieci OSDp | Dowolnie | Harmonogram dyspozycyjności przekazywany dla horyzontu od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Plan pracy MEE przekazywany dla horyzontu dobowego (od doby d do doby d+9) <br /><br /> Pojemność użytkowa MEE przekazywana dla horyzontu od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Polecenia ruchowe OSD dla horyzontu dobowego (od doby bieżącej do doby d+9) |
| Właściciel | MEE w sieci OSP | Dowolnie | Niedostępność (postój, ubytek dodatni, ubytek ujemny) dla horyzontu od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Niesprawność regulacji pierwotnej, wtórnej lub ARNE (w przypadku świadczenia usług) od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Plan pracy MEE przekazywany dla horyzontu dobowego (od doby d do doby d+9) <br /><br /> Pojemność użytkowa MEE przekazywana dla horyzontu od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Ograniczenia zdolności regulacji mocy biernej od doby bieżącej do 5 lat (60 miesięcy) naprzód |
| Właściciel | pompa | Dowolnie | Niedostępność (postój, ubytek dodatni, ubytek ujemny) dla horyzontu od doby bieżącej do 5 lat (60 miesięcy) naprzód <br /><br /> Plan pracy pompy przekazywany dla horyzontu dobowego (od doby bieżącej do doby d+9) |
OSDp | Linia wymiany <br /> Obiekt wymiany (grupa linii wymiany) | Nie dotyczy | Grafik planowanego salda wymiany nierównoległej realizowanej poprzez sieć 110 kV przekazywany przez OSDp dla horyzontu 5-letniego, rocznego i dobowego |

<br>

## Komunikaty i usługi
W ramach kanału B2B przewidziana jest komunikacja dwustronna. Jest to realizowane za pomocą Server-Sent Events (SSE) dla powiadomień oraz REST dla wymiany danych.
SSE uzupełnia komunikację REST o możliwość powiadamiania zgłaszająch OSDp i Właścicieli o zmianach statusu ich zgłoszeń oraz o zmianach niedyspozycyjności, które nastąpiły poza kanałem B2B.


### Zgłaszanie danych planistycznych (niedyspozycyjności oraz danych grafikowych)
Informacje biznesowe w kanale B2B są przekazywane w postaci komunikatów. Komunikat elektroniczny stanowi sformalizowany co do struktury oraz formatu zbiór danych przesyłanych jako komunikat na potrzeby wymiany informacji planistycznych dotyczących wymienionych wyżej zasobów.
Format komunikatów obowiązujących w kanale B2B jest zgodny ze standardem opisu JSON.

[Komunikat postoju](docs/komunikat%20zg%C5%82oszenia%20postoju.md)
                    
[Komunikat ubytku](docs/komunikat%20zg%C5%82oszenia%20ubytku.md)

[Komunikat niesprawności układu regulacji](docs/komunikat%20zgłoszenia%20niesprawności.md)

[Komunikat ograniczenia zdolności regulacji mocy biernej](docs/komunikat%20zg%C5%82oszenia%20ograniczenia%20zdolno%C5%9Bci%20regulacji%20mocy%20biernej.md)

[Komunikat harmonogramu dyspozycyjności](docs/komunikat%20zgłoszenia%20harmonogramu%20dyspozycyjności.md)

[Komunikat pojemności użytkowej](docs/komunikat%20zgłoszenia%20pojemności%20użytkowej.md)

[Komunikat planu pracy](docs/komunikat%20zgłoszenia%20planu%20pracy.md)

[Komunikat poleceń ruchowych OSD](docs/komunikat%20zgłoszenia%20poleceń%20ruchowych%20OSD.md)

[Komunikat salda wymiany](docs/komunikat%20zgłoszenia%20salda%20wymiany.md)

### Powiadamianie o zmianie danych planistycznych
[Powiadomienia i odpowiedzi na zgłoszenia](docs/komunikat%20odpowiedzi.md)

### Udostępnianie danych planistycznych
[Plan niedostępności - postoje dla zasobu w zadanym okresie oraz szczegóły wskazanego postoju](docs/komunikat%20postoje.md)

[Plan niedostępności - ubytki dla zasobu w zadanym okresie oraz szczegóły wskazanego ubytku](docs/komunikat%20ubytki.md)

[Plan niesprawności układów regulacji w zadanym okresie oraz szczegóły wskazanej niesprawności](docs/komunikat%20niesprawności.md)

[Ograniczenia zdolności regulacji mocy biernej](docs/komunikat%20ograniczenia%20zdolno%C5%9Bci%20regulacji%20mocy%20biernej.md)

[Harmonogram dyspozycyjności dla zasobu w zadanym okresie](docs/komunikat%20harmonogram%20dyspozycyjności.md)

[Pojemność użytkowa dla zasobu w zadanym okresie](docs/komunikat%20pojemność%20użytkowa.md)

[Plan pracy dla zasobu w zadanym okresie](docs/komunikat%20plan%20pracy.md)

[Polecenia ruchowe OSD dla zasobu w zadanym okresie](docs/komunikat%20polecenia%20ruchowe%20OSD.md)

[Saldo wymiany dla linii wymiany w zadanym okresie](docs/komunikat%20saldo%20wymiany.md)

<br>

### Usługi umożliwiające wymianę danych planistycznych
W celu realizacji procesu zgłaszania danych planistycznych udostępnione są niżej wymienione usługi (serwisy), szczegółowo opisane w ramach API. 

Serwisy umożliwiające zgłoszenie danych planistycznych:
* postój - /pwdp/api/v1/outage-submissions
* ubytek - /pwdp/api/v1/derate-submissions
* niesprawność układu regulacji - /pwdp/api/v1/control-malfunction-submissions
* ograniczenia zdolności regulacji mocy biernej - /pwdp/api/v1/reactive-limit-submissions
* harmonogram dyspozycyjności - /pwdp/api/v1/availability-submissions
* pojemność użytkowa - /pwdp/api/v1/storage-capacity-submissions
* plan pracy - /pwdp/api/v1/schedule-submissions
* polecenia ruchowe OSD - /pwdp/api/v1/dispatch-instruction-submissions
* saldo wymiany nierównoległej - /pwdp/api/v1/exchange-schedule-submissions

Serwisy udostępniające dane planistyczne:
* status przetwarzania zgłoszenia - /pwdp/api/v1/submissions/{serverMsgId}/status
* postoje dla zasobu w zadanym okresie - /pwdp/api/v1/resources/{mainResourceMrid}/outages
* dane wskazanego postoju dla zasobu - /pwdp/api/v1/resources/{mainResourceMrid}/outages/{unavailabilityMrid}
* ubytki dla zasobu w zadanym okresie - /pwdp/api/v1/resources/{mainResourceMrid}/derates
* dane wskazanego ubytku dla zasobu - /pwdp/api/v1/resources/{mainResourceMrid}/derates/{unavailabilityMrid}
* niesprawności układu regulacji dla zasobu w zadanym okresie - /pwdp/api/v1/resources/{mainResourceMrid}/control-malfunctions
* dane wskazanej niesprawności dla zasobu - /pwdp/api/v1/resources/{mainResourceMrid}/control-malfunctions/{unavailabilityMrid}
* ograniczenia zdolności regulacji mocy biernej dla zasobu w zadanym okresie - /pwdp/api/v1/resources/{mainResourceMrid}/reactive-limits
* harmonogram dyspozycyjności dla zasobu w zadanym okresie - /pwdp/api/v1/resources/{mainResourceMrid}/availabilities
* poziomy pojemności użytkowej dla magazynu w zadanym okresie - /pwdp/api/v1/resources/{mainResourceMrid}/storage-capacities
* plan pracy dla zasobu w zadanym okresie - /pwdp/api/v1/resources/{mainResourceMrid}/schedules
* polecenia ruchowe OSD dla zasobu w zadanym okresie - /pwdp/api/v1/resources/{mainResourceMrid}/dispatch-instructions
* saldo wymiany nierównoległej dla zasobu w zadanym okresie - /pwdp/api/v1/resources/{mainResourceMrid}/exchange-schedules

<br>

### Statusy zgłoszeń
Zgłoszenia danych planistycznych są odbierane z kanału B2B i weryfikowane pod kątem poprawności formalnej i w podstawowym zakresie biznesowym. 

Po pozytywnym przejściu weryfikacji zgłoszenie uzyskuje status **Pozyskane (SUBMITTED)** i jest przekazywane do systemu planowania koordynacyjnego. Tam przeprowadzana jest dalsza weryfikacja, w wyniku której prawidłowe zgłoszenie uzyskuje status **Przyjęte (APPROVED)**.

Uwaga: Zakres wartości niektórych pól dostępny w słownikach stosowanych w ramach schematu może być na dalszym etapie ograniczony za pomocą reguł poprawności z powodu wymogów biznesowych.

Zgłoszenie nieprawidłowe otrzymuje status **Odrzucone (REJECTED)**.

<br>

## Zasady dotyczące zgłaszania danych planistycznych

### Kompletność danych w zgłoszeniach
W kanale B2B oczekiwane jest zgłaszanie danych planistycznych, które są kompletne w okresie zadeklarowanym w zgłoszeniu. Dotyczy to zarówno danych o charakterze okresowym (niedyspozycyjności czyli postoje, ubytki, niesprawności układu regulacji) jak i danych grafikowych. 

W przypadku danych grafikowych weryfikacja kompletności danych jest ściśle związana z wymagalnością przekazywanych serii danych. Kompletność zgłoszenia wymaga wypełnienia wartości dla wszystkich wymaganych serii danych. Dodatkowo na wymagalność danych wpływa zarówno rodzaj poszczególnych serii danych jak i konfiguracja samego obiektu. Oznacza to, że dane określone jako wymagane, są oczekiwane tylko w tym okresie, w którym obiekt jest dostępny albo w którym odpowiedni parametr tego obiektu jest ustawiony tak, że uzasadnia obecność powiązanej z nim serii danych. 

Kompletność danego zgłoszenia danych grafikowych nie wymusza podawania serii danych uzupełniających (niewymaganych). Mogą one być pominięte albo mogą nie zawierać wartości w części lub w całym zadanym przez zgłoszenie okresie. Brak wartości w tych seriach, ew. podawanie wartości pustych (null) oznaczających brak określonej wartości, jest dopuszczalny i stanowi prawidłowy sposób reprezentacji danych w sytuacji, gdy wartości nie występują albo mają zostać usunięte.

Okres podany dla całego zgłoszenia danych grafikowych odnosi się ostatecznie zarówno do serii danych wymaganych, jak i do serii uzupełniających. Przyjęcie zgłoszenia powoduje zatem, że dotychczasowe dane w tym okresie zostają w pełni zastąpione nowoprzyjętymi danymi, w szczególności niepodane wartości powodują usunięcie wartości dotychczasowych w danych punktach czasowych. W każdym zgłoszeniu należy zatem określić tylko taki okres dla danych, w jakim mają one zostać wymienione.

W tabeli poniżej podano parametry zgłoszeń, w szczególności wskazanie na serie danych, dla których wartości są wymagane oraz na serie danych, dla których wartości mogą nie wystąpić (uzupełniające). Wymagalność jest uzależniona od uzasadniającej ją konfiguracji obiektu, zatem w sytuacji zmiany tej konfiguracji w okresie zgłoszenia możliwa jest seria danych krótsza względem okresu całego zgłoszenia.


| Kod typu dokumentu (pole type) | Rodzaj komunikatu | Kod szczegółowy (pole businessType) | Rodzaj danych | Seria danych wymagana | Kompletność serii danych <br /><br /> Dopuszczalne puste wartości (null) | Kierunek | Typ krzywej | Jednostka miary | Rozdzielczość | Dziedzina wielkości<br /><br /> Dokładność |
|---|---|---|---|---|---|---|---|---|---|---|
| POS | Postój | POS | Postój | Nie dotyczy | Nie dotyczy | Wymagany (wartości GENERATION, CONSUMPTION, TOTAL) | - <br /> A01 dla UD | - <br /> MAW dla UD | - <br /> PT15M (kwadrans) dla UD | - <br /> <0, 99999.999> dla UD <br /> 3 miejsca po przecinku |
| UBT | Ubytek | UBTD | Ubytek dodatni | Nie dotyczy | Nie dotyczy | Wymagany (wartości GENERATION, CONSUMPTION) | A03 | MAW | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> PT5M (5 minut)<br /> PT1M (1 minuta)<br /> | nieujemne <br /> 3 miejsca po przecinku |
|  |  | UBTU | Ubytek ujemny | Nie dotyczy | Nie dotyczy | Wymagany (wartości GENERATION, CONSUMPTION) | A03 | MAW | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> PT5M (5 minut)<br /> PT1M (1 minuta)<br /> | nieujemne <br /> 3 miejsca po przecinku |
| NUR | Niesprawność układu regulacji | FCRG | Niesprawność układu regulacji FCR_G - rezerwa utrzymania częstotliwości w górę (FCR<sup>G</sup>, regulacja pierwotna) | Nie dotyczy | Nie dotyczy | Wymagany tylko dla zasobów dwukierunkowych (wartości GENERATION, CONSUMPTION) | Nie dotyczy | Nie dotyczy | Nie dotyczy | Nie dotyczy |
|  |  | FCRD | Niesprawność układu regulacji FCR_D - rezerwa utrzymania częstotliwości w dół (FCR<sup>D</sup>, regulacja pierwotna) | Nie dotyczy | Nie dotyczy | Wymagany tylko dla zasobów dwukierunkowych (wartości GENERATION, CONSUMPTION) | Nie dotyczy | Nie dotyczy | Nie dotyczy | Nie dotyczy |
|  |  | AFRG | Niesprawność układu regulacji aFRR_G - rezerwa odbudowy częstotliwości z aktywacją automatyczną w górę (aFRR<sup>G</sup>, regulacja wtórna) | Nie dotyczy | Nie dotyczy | Wymagany tylko dla zasobów dwukierunkowych (wartości GENERATION, CONSUMPTION) | Nie dotyczy | Nie dotyczy | Nie dotyczy | Nie dotyczy |
|  |  | AFRD | Niesprawność układu regulacji aFRR_D - rezerwa odbudowy częstotliwości z aktywacją automatyczną w dół (aFRR<sup>D</sup>, regulacja wtórna) | Nie dotyczy | Nie dotyczy | Wymagany tylko dla zasobów dwukierunkowych (wartości GENERATION, CONSUMPTION) | Nie dotyczy | Nie dotyczy | Nie dotyczy | Nie dotyczy |
|  |  | MFRG | Niesprawność układu regulacji mFRRd_G - rezerwa odbudowy częstotliwości z aktywacją nieautomatyczną typu bezpośredniego w górę (mFRRd<sup>G</sup>, regulacja wtórna) | Nie dotyczy | Nie dotyczy | Wymagany tylko dla zasobów dwukierunkowych (wartości GENERATION, CONSUMPTION) | Nie dotyczy | Nie dotyczy | Nie dotyczy | Nie dotyczy |
|  |  | MFRD | Niesprawność układu regulacji mFRRd_D - rezerwa odbudowy częstotliwości z aktywacją nieautomatyczną typu bezpośredniego w dół (mFRRd<sup>D</sup>, regulacja wtórna) | Nie dotyczy | Nie dotyczy | Wymagany tylko dla zasobów dwukierunkowych (wartości GENERATION, CONSUMPTION) | Nie dotyczy | Nie dotyczy | Nie dotyczy | Nie dotyczy |
|  |  | ARNE | Niesprawność układu regulacji ARNE - zdolność regulacji mocy biernej | Nie dotyczy | Nie dotyczy | Brak | Nie dotyczy | Nie dotyczy | Nie dotyczy | Nie dotyczy |
| HRM | Harmonogram dyspozycyjności | MINE | Harmonogram dyspozycyjności - Możliwe minimum dyspozycyjności elektrownianej (określone na koniec poszczególnych OREB) | Tak <br /><br />(w każdym istniejącym kierunku) | Kompletne | Wymagany (wartości GENERATION, CONSUMPTION) | A03 | MAR | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
|  |  | MAXE | Harmonogram dyspozycyjności - Dostępne maksimum dyspozycyjności elektrownianej (określone na koniec poszczególnych OREB) | Tak <br /><br /> (w każdym istniejącym kierunku) | Kompletne | Wymagany (wartości GENERATION, CONSUMPTION) | A03 | MAR | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
|  |  | MINS | Harmonogram dyspozycyjności - Możliwe minimum dyspozycyjności sieciowej (określone na koniec poszczególnych OREB) | Tak <br /><br /> (w każdym istniejącym kierunku) | Kompletne | Wymagany (wartości GENERATION, CONSUMPTION) | A03 | MAR | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
|  |  | MAXS | Harmonogram dyspozycyjności - Dostępne maksimum dyspozycyjności sieciowej (określone na koniec poszczególnych OREB) | Tak <br /><br /> (w każdym istniejącym kierunku) | Kompletne | Wymagany (wartości GENERATION, CONSUMPTION) | A03 | MAR | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
| ORMB | Ograniczenia zdolności regulacji mocy biernej | PINMN | Minimum mocy indukcyjnej w stanie pracy zasobu | Nie | Mogą być puste | Wymagany (wartości GENERATION, CONSUMPTION, TOTAL — w zależności od technologii zasobu) | A03 | MAW | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
|  |  | PINMX | Maksimum mocy indukcyjnej w stanie pracy zasobu | Nie | Mogą być puste | Wymagany (wartości GENERATION, CONSUMPTION, TOTAL — w zależności od technologii zasobu) | A03 | MAW | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
|  |  | PCPMN | Minimum mocy pojemnościowej w stanie pracy zasobu | Nie | Mogą być puste | Wymagany (wartości GENERATION, CONSUMPTION, TOTAL — w zależności od technologii zasobu) | A03 | MAW | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
|  |  | PCPMX | Maksimum mocy pojemnościowej w stanie pracy zasobu | Nie | Mogą być puste | Wymagany (wartości GENERATION, CONSUMPTION, TOTAL — w zależności od technologii zasobu) | A03 | MAW | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
|  |  | KINMN | Minimum mocy indukcyjnej w stanie kompensacji zasobu | Nie | Mogą być puste | Wymagany (wartość TOTAL) | A03 | MAR | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
|  |  | KINMX | Maksimum mocy indukcyjnej w stanie kompensacji zasobu | Nie | Mogą być puste | Wymagany (wartość TOTAL) | A03 | MAR | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
|  |  | KCPMN | Minimum mocy pojemnościowej w stanie kompensacji zasobu | Nie | Mogą być puste | Wymagany (wartość TOTAL) | A03 | MAR | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
|  |  | KCPMX | Maksimum mocy pojemnościowej w stanie kompensacji zasobu | Nie | Mogą być puste | Wymagany (wartość TOTAL) | A03 | MAR | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
| PUZ | Pojemność użytkowa (magazynu) | PUZ | Pojemność użytkowa (magazynu) | Tak | Kompletne | Brak | A03 | MWH | PT60M (1 godzina)<br /> PT15M (kwadrans)<br /> | nieujemne |
| PLP | Plan pracy | MCSR | Plan pracy - średnie wielkości mocy czynnej netto wprowadzanej do sieci/pobieranej z sieci w poszczególnych OREB | Tak <br /><br /> (w każdym istniejącym kierunku) | Kompletne | Wymagany (wartości GENERATION, CONSUMPTION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
|  |  | MCKN | Plan pracy - wielkości mocy czynnej netto wprowadzanej do sieci/pobieranej z sieci na koniec poszczególnych OREB | Tak <br /><br /> (w każdym istniejącym kierunku) | Kompletne | Wymagany (wartości GENERATION, CONSUMPTION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
|  |  | MCSO | Plan pracy - średnie wielkości mocy czynnej netto wprowadzanej do sieci/pobieranej z sieci w poszczególnych OREB z uwzględnieniem polecenia ruchowego OSD | Nie | Mogą być puste | Wymagany (wartości GENERATION, CONSUMPTION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
|  |  | MCKO | Plan pracy - wielkości mocy czynnej netto wprowadzanej do sieci/pobieranej z sieci na koniec poszczególnych OREB z uwzględnieniem polecenia ruchowego OSD | Nie | Mogą być puste | Wymagany (wartości GENERATION, CONSUMPTION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
|  |  | ZNSR | Plan pracy - znacznik określający, czy wielkości generacji mocy czynnej wprowadzone do sieci w poszczególnych OREB przez MWE odzwierciedlają generację mocy czynnej netto odpowiadającą potencjałowi generacji MWE wynikającemu z warunków meteorologicznych <br /> (1 - wielkość generacji mocy czynnej wprowadzonej do sieci odpowiada potencjałowi generacji MWE wynikającemu z warunków meteorologicznych; 0 - wielkość generacji mocy czynnej wprowadzonej do sieci nie odpowiada potencjałowi generacji MWE wynikającemu z warunków meteorologicznych) <br /><br /> (dotyczy tylko MWE typu B, C, D, dane w kierunku generacji) | Tak | Kompletne | Brak | A01 | FLAG | PT15M (kwadrans) | 0, 1 |
|  |  | ZNKN | Plan pracy - znacznik określający, czy wielkości generacji mocy czynnej wprowadzone do sieci na koniec OREB przez MWE odzwierciedlają generację mocy czynnej netto odpowiadającą potencjałowi generacji MWE wynikającemu z warunków meteorologicznych <br /> (1 - wielkość generacji mocy czynnej wprowadzonej do sieci odpowiada potencjałowi generacji MWE wynikającemu z warunków meteorologicznych; 0 - wielkość generacji mocy czynnej wprowadzonej do sieci nie odpowiada potencjałowi generacji MWE wynikającemu z warunków meteorologicznych) <br /><br /> (dotyczy tylko MWE typu B, C, D, dane w kierunku generacji) | Tak | Kompletne | Brak | A01 | FLAG | PT15M (kwadrans) | 0, 1 |
|  |  | AGSR | Plan pracy - średnie wielkości generacji mocy czynnej netto wytwarzanej w danym OREB przez MWE na własne potrzeby  <br /><br /> (dotyczy tylko MWE typu B, C, D ze znacznikiem „autogeneracja”, dane w kierunku generacji) | Dla MWE z autogeneracją → Tak | Kompletne | Wymagany (wartość GENERATION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
|  |  | AGKN | Plan pracy - wielkości generacji mocy czynnej netto wytwarzane na koniec poszczególnych OREB przez MWE na własne potrzeby <br /><br /> (dotyczy tylko MWE typu B, C, D ze znacznikiem „autogeneracja”, dane w kierunku generacji) | Dla MWE z autogeneracją → Tak | Kompletne | Wymagany (wartość GENERATION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
|  |  | MCSD | Plan pracy - średnie wielkości generacji mocy czynnej netto MWE w poszczególnych OREB, określające potencjał generacji MWE wynikający z warunków meteorologicznych i z mocy dyspozycyjnej elektrownianej MWE <br /><br /> (dotyczy tylko MWE PPM - w kategorii FW, PV lub układ hybrydowy, w tym dla poszczególnych elementów tego układu, dane w kierunku generacji) | Dla MWE, które jest PPM → Tak | Kompletne | Wymagany (wartość GENERATION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
|  |  | MCKD | Plan pracy - wielkości generacji mocy czynnej netto MWE na koniec poszczególnych OREB, określające potencjał generacji MWE wynikający z warunków meteorologicznych i z mocy dyspozycyjnej elektrownianej MWE (dotyczy tylko PPM typu FW, PPM typu PV i PPM typu układ hybrydowy, w tym dla poszczególnych elementów tego układu) <br /><br /> (dotyczy tylko MWE PPM - w kategorii FW, PV lub układ hybrydowy, w tym dla poszczególnych elementów tego układu, dane w kierunku generacji) | Dla MWE, które jest PPM → Tak | Kompletne | Wymagany (wartość GENERATION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
|  |  | MCSZ | Plan pracy - średnie wielkości generacji mocy czynnej netto MWE w poszczególnych OREB, określające potencjał generacji MWE wynikający z warunków meteorologicznych i z mocy zainstalowanej MWE (dotyczy tylko PPM typu FW, PPM typu PV i PPM typu układ hybrydowy, w tym dla poszczególnych elementów tego układu) <br /><br /> (dotyczy tylko MWE PPM - w kategorii FW, PV lub układ hybrydowy, w tym dla poszczególnych elementów tego układu, dane w kierunku generacji) | Dla MWE, które jest PPM → Tak | Kompletne | Wymagany (wartość GENERATION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
|  |  | MCKZ | Plan pracy - wielkości generacji mocy czynnej netto MWE na koniec poszczególnych OREB, określające potencjał generacji MWE wynikający z warunków meteorologicznych i z mocy zainstalowanej MWE <br /><br /> (dotyczy tylko MWE PPM - w kategorii FW, PV lub układ hybrydowy, w tym dla poszczególnych elementów tego układu, dane w kierunku generacji) | Dla MWE, które jest PPM → Tak | Kompletne | Wymagany (wartość GENERATION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
|  |  | PWP | Plan pracy - znacznik (0, 1, 2) planowanej pracy wymuszonej, w przypadku MEE dotyczy trybu rozładowania <br /><br /> (dotyczy tylko MWE typu D oraz MEE w sieci OSP, dane w kierunku generacji) | Nie | Kompletne | Wymagany (wartość GENERATION) | A01 | FLAG | PT15M (kwadrans) | 0, 1, 2 |
|  |  | SNAL | Stan naładowania MEE na koniec poszczególnych OREB <br /><br /> (dotyczy tylko MEE) | Dla MEE → Tak | Kompletne | Brak | A01 | MWH | PT15M (kwadrans) | nieujemne |
| PRU | Polecenia ruchowe OSD | OMAX | Polecenia ruchowe OSD - Pmax wielkości mocy czynnej netto w poszczególnych OREB wynikający z poleceń ruchowych OSDp | Nie | Mogą być puste | Wymagany (wartości GENERATION, CONSUMPTION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
|  |  | OMIN | Polecenia ruchowe OSD - Pmin wielkości mocy czynnej netto w poszczególnych OREB wynikający z poleceń ruchowych OSDp | Nie | Mogą być puste | Wymagany (wartości GENERATION, CONSUMPTION) | A01 | MAW | PT15M (kwadrans) | nieujemne |
| WYM | Saldo wymiany | WYM | Saldo wymiany <br /><br /> (dotyczy tylko linii wymiany) | Tak | Kompletne | Brak | A01 | MAW | P1M (1 miesiąc)<br /> P1D (1 dzień)<br /> PT60M (1 godzina)<br /> | z dokładnością do 3 miejsc po przecinku |


### Nadpisywanie danych ze zgłoszeń grafikowych
Wartości z kolejnego zgłoszenia grafikowego dotyczącego tego samego zasobu i nakładającego się okresu zgłoszenia nadpisują odpowiednie wartości z tych samych punktów czasowych pozyskane z wcześniejszego zgłoszenia. Dotyczy to zarówno wymaganych serii danych grafikowych, jak i  serii uzupełniających. Dodatkowo serie uzupełniające mogą wystąpić bez podanych wartości. W takim przypadku jeśli na dany moment była uprzednio zanotowana jakaś wartość, a przyjęte nowe zgłoszenie przekazuje na ten sam moment wartość pustą, oznacza to, że poprzednia wartość przestaje obowiązywać (jest usuwana) i na ten moment występuje brak wartości.

Również jeśli w serii danych (niewymaganych) o zdefiniowanym okresie we wcześniejszym zgłoszeniu przekazano wartości, a w kolejnym zgłoszeniu pominięto tę serię danych, to wartości z poprzednio podanej serii są usuwane. Tym samym kolejne zgłoszenie od nowa definiuje grafiki w całym okresie zgłoszenia, który jest w nim zadeklarowany (dla zasobu i ew. jego składowych, we wszystkich dostępnych dla niego kierunkach).

W szczególnym przypadku zgłoszenia poleceń ruchowych OSD albo ograniczeń zdolności regulacji mocy biernej, jeśli w zadanym horyzoncie występuje całkowity brak takich danych oraz nie ma potrzeby wycofywania poprzednio zgłoszonych danych, to nie jest wskazane wysyłanie zgłoszenia "pustego", tj. bez podanych serii danych lub przekazanie serii danych bez wartości czy ze wszystkimi wartościami pustymi (null). Natomiast jeśli występuje potrzeba całkowitego wycofania poprzednio zgłoszonych danych, możliwe jest wysłanie zgłoszenia "pustego", czyli bez podania żadnej serii danych.


### Zasady przy opisie parametrów zgłoszeń
Każdy przedział dat w zgłoszeniach jest traktowany jako lewostronnie otwarty a prawostronnie domknięty, czyli jest brany pod uwagę bez swojego punktu początkowego, natomiast z uwzględnieniem punktu końcowego przedziału. Powoduje to w szczególności, że niedyspozycyjności następujące kolejno po sobie zgłasza się przykładowo: pierwszą od 5:00 do 7:00 oraz drugą od 7:00 do 9:00. Obie niedyspozycyjności są styczne, ale nie nakładają się. Godzina 7:00 jest uwzględniona w pierwszej niedyspozycyjności.

W zgłoszeniach należy uwzględnić, że daty, a także punkty zmiany powinny być interpretowane jako planowane albo wykonane względem przewidywanego czasu wysłania, a dokładniej względem stempla czasowego, jaki zgłoszenie otrzymuje przy jego pozyskaniu.

W zgłoszeniach należy ponadto uwzględnić, aby przedziały dat czy punkty zmiany określać z dokładnością co najwyżej do pełnych minut, tj. nie podawać dodatkowych (niezerowych) sekund czy milisekund.

Zgłoszenia niedyspozycyjności o tym samym mRID będą dodatkowo identyfikowane poprzez kolejność stempla czasowego oraz numer porządkowy zgłoszenia. Numer porządkowy zgłoszenia powinien być rosnący. Niedyspozycyjność powstała na skutek inicjalnego (przyjętego) zgłoszenia może być wielokrotnie korygowana (za każdym razem poprzez zgłoszenie z kolejnym numerem porządkowym). 

Niedyspozycyjność może zostać wycofana. Po przyjęciu zgłoszenia wycofania nie jest możliwe dalsze odwoływanie się do tej niedyspozycyjności (dalsze modyfikacje). W to miejsce można zgłosić nową niedyspozycyjność.

mRID to pole identyfikacyjne, którego wartość jest ustalona według zasad tworzenia identyfikatorów unikalnych globalnie (algorytm GUID). Identyfikator składa się 5 grup cyfr heksadecymalnych, ew. prefiksu "\_" w przypadku zasobów, a także łączników. Można go przedstawić w postaci schematu ilustrującego, ile cyfr jest w danej grupie: (\_)8-4-4-4-12. 

W przypadku udostępniania danych w pytaniu wskazywany jest obiekt (zawsze chodzi o cały zasób, nie składową) oraz przedział dat, który definiuje okres, w jakim będą udostępniane dane. W szczególności dla danych grafikowych udostępniane są dane tylko w okresie zdefiniowanym w pytaniu. Dane mogą dotyczyć całego zasobu, a także jego składowych (w przypadku, gdy jest to MWE z wieloma składowymi).

W ramach planów pracy wartości określane jako wielkości mocy czynnej z uwzględnieniem polecenia ruchowego OSD nie powinny uwzględniać poleceń redysponowania OSP.


<br>

## Przebieg komunikacji

### Zgłaszanie niedyspozycyjności (REST + SSE)

Poniższy opis przebiegu (workflow) dotyczy zgłaszania:
 - postojów,
 - ubytków,
 - niesprawności układów regulacji.

#### Opis na przykładzie zgłoszenia postoju:

1. Klient łączy się ze strumieniem SSE (`GET .../planning/{entityId}/stream`)
2. Serwer wysyła zdarzenie `connected` potwierdzające połączenie
3. Co 30 sekund serwer wysyła zdarzenie `heartbeat` podtrzymujące połączenie
4. Klient przesyła zgłoszenie (`POST .../outage-submissions`)
5. Po przetworzeniu zgłoszenia serwer wysyła zdarzenie informujące o rezultacie przetworzenia (`SUBMISSION_APPROVED`, `SUBMISSION_REJECTED`)
6. Klient ma możliwość pobrania szczegółów odpowiedzi na zgłoszenie (`GET .../submissions/{serverMsgId}/status`)
6. Po aktualizacji planu serwer wysyła powiadomienie o zmianie w planie zgodnie z zgłoszeniem (`OUTAGE_CREATED`, `OUTAGE_MODIFIED`, `OUTAGE_WITHDRAWN`)
7. Klient ma możliwość pobrania szczegółów postoju w aktualnym planie (`GET .../resources/{mainResourceMrid}/outages/{UnavailablityMrid}`)

**Wznowienie połączenia:** W przypadku zerwania połączenia SSE, klient MUSI ponownie połączyć się z nagłówkiem `Last-Event-ID` zawierającym ID ostatniego otrzymanego zdarzenia. Serwer wznowi transmisję od pominiętych zdarzeń.


#### Diagram sekwencji - na przykładzie zgłoszenia postoju

```mermaid
sequenceDiagram
    participant Client as Podmiot (OSDp/Właściciel)
    participant API as B2B REST API
    participant Backend as Backend service

    Note over Client,Backend: Połączenie do strumienia powiadomień
    Client->>API: GET .../planning/{entityId}/stream
    API-->>Client: SSE: connected (connectionId, timestamp)

    loop Co 30 sekund
        API-->>Client: SSE: heartbeat (timestamp)
    end

    Note over Client,Backend: Zgłoszenie postoju
    Client->>API: POST .../outage-submissions
    API-->>Client: 202 Accepted
    Backend->>Backend: Przetworzenie zgłoszenia
    
    Note over Client,Backend: Powiadomienie o przetworzeniu zgłoszenia
    alt APPROVED  
      API-->>Client: SSE: SUBMISSION_APPROVED (serverMsgId)
    else REJECTED 
      API-->>Client: SSE: SUBMISSION_REJECTED (serverMsgId)
    end    
    Client->>API: GET .../submissions/{serverMsgId}/status
    
    Note over Client,Backend: Powiadomienie o aktualizacji postoju w planie
    alt CREATED  
      API-->>Client: SSE: OUTAGE_CREATED (unavailabilityMrid)
    else MODIFIED 
      API-->>Client: SSE: OUTAGE_MODIFIED (unavailabilityMrid)
    else WITHDRAWN
      API-->>Client: SSE: OUTAGE_WITHDRAWN (unavailabilityMrid)
    end    
    Client->>API: GET .../resources/{mainResourceMrid}/outages/{unavailablityMrid}
```

### Proces zgłaszania danych grafikowych (REST + SEE)

Poniższy opis przebiegu (workflow) dotyczy zgłaszania:
- planów pracy,
- harmonogramów dyspozycyjności,
- pojemności użytkowej magazynów,
- poleceń ruchowych OSD,
- salda wymiany dla linii wymiany 110kV
- ograniczenia zdolności regulacji mocy biernej

#### Opis na przykładzie zgłoszenia planu pracy

1. Klient łączy się ze strumieniem SSE (`GET .../planning/{entityId}/stream`)
2. Serwer wysyła zdarzenie `connected` potwierdzające połączenie
3. Co 30 sekund serwer wysyła zdarzenie `heartbeat` podtrzymujące połączenie
4. Klient przesyła zgłoszenie (`POST .../schedule-submissions`)
5. Po przetworzeniu zgłoszenia serwer wysyła zdarzenie informujące o rezultacie przetworzenia (`SUBMISSION_APPROVED`, `SUBMISSION_REJECTED`)
6. Klient ma możliwość pobrania szczegółów odpowiedzi na zgłoszenie (`GET .../submissions/{serverMsgId}/status`)
7. Klient ma możliwość pobrania szczegółów planu pracy w aktualnym planie (`GET .../resources/{mainResourceMrid}/schedules`)

**Wznowienie połączenia:** W przypadku zerwania połączenia SSE, klient MUSI ponownie połączyć się z nagłówkiem `Last-Event-ID` zawierającym ID ostatniego otrzymanego zdarzenia. Serwer wznowi transmisję od pominiętych zdarzeń.


#### Diagram sekwencji - na przykładzie zgłoszenia planu pracy

```mermaid
sequenceDiagram
    participant Client as Podmiot (OSDp/Właściciel)
    participant API as B2B REST API
    participant Backend as Backend service

    Note over Client,Backend: Połączenie do strumienia powiadomień
    Client->>API: GET .../planning/{entityId}/stream
    API-->>Client: SSE: connected (connectionId, timestamp)

    loop Co 30 sekund
        API-->>Client: SSE: heartbeat (timestamp)
    end

    Note over Client,Backend: Zgłoszenie planu pracy
    Client->>API: POST .../schedule-submissions
    API-->>Client: 202 Accepted
    Backend->>Backend: Przetworzenie zgłoszenia
    
    Note over Client,Backend: Powiadomienie o przetworzeniu zgłoszenia
    alt APPROVED  
      API-->>Client: SSE: SUBMISSION_APPROVED (serverMsgId)
    else REJECTED 
      API-->>Client: SSE: SUBMISSION_REJECTED (serverMsgId)
    end    
    Client->>API: GET .../submissions/{serverMsgId}/status
    
    Note over Client,Backend: Pobranie informacji o planie pracy w aktualnym planie
    opt
      Client->>API: GET .../resources/{mainResourceMrid}/schedules
    end    

```

