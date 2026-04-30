# **Powiadomienia i Odpowiedzi**

## Otwarcie strumienia komunikacji
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca komunikatu | OSDp (Operator Systemu Dystrybucyjnego), Właściciel obiektu przyłączonego do sieci OSP |
| Odbiorca komunikatu | OSP (Operator Systemu Przesyłowego) |


### Charakterystyka komunikatu
Podmiot chcący zgłosić dane planistyczne zgodnie ze specyfiką komunikacji REST + SSE inicjuje połączenie. Jest to działanie przygotowawcze wobec właściwej wymiany danych.
Następnie zgłaszający może zostać poinformowany o zdarzeniu, którym jest zmiana statusu zgłoszenia (jeśli zostało wysłane zgłoszenie) albo zmiana niedyspozycyjności spoza kanału B2B.


## Endpointy API
---
### GET `.../planning/{entityId}/stream`
Otwarcie strumienia Server-Sent Events (SSE) dla danego podmiotu.
| Parametr | Typ | Lokalizacja | Wymagany | Opis |
|----------|-----|-------------|:--------:|------|
| `entityId` | integer| path | tak | Identyfikator podmiotu |
| `Last-Event-ID` | string | header | nie | ID ostatniego otrzymanego zdarzenia (do wznowienia) |

**operationId:**  `subscribeToEntityStream`
**Tag:** SSE Streaming
**Content-Type:**  `text/event-stream`

#### Typy zdarzeń SSE
| Zdarzenie | Opis | Częstotliwość |
|-----------|------|---------------|
| `connected` | Potwierdzenie nawiązania połączenia SSE | Raz po połączeniu |
| `heartbeat` | Podtrzymanie połączenia | Co 30 sekund |
| `SUBMISSION_APPROVED` | Powiadomienie o przyjęciu danych ze zgłoszenia do planu | Gdy zgłoszenie zostało przyjęte do planu |
| `SUBMISSION_REJECTED` | Powiadomienie o odrzuceniu zgłoszenia | Gdy zgłoszenie zostało odrzucone |
| `OUTAGE_CREATED` | Powiadomienie o nowym postoju w planie | Gdy do planu został dodany nowy postój |
| `OUTAGE_MODIFIED` | Powiadomienie o modyfikacji postoju w planie | Gdy postój w planie uległ modyfikacji |
| `OUTAGE_WITHDRAWN` | Powiadomienie o wycofaniu postoju z planu | Gdy postój został wycofany z planu |
| `DERATE_CREATED` | Powiadomienie o nowym ubytku w planie | Gdy do planu został dodany nowy ubytek |
| `DERATE_MODIFIED` | Powiadomienie o modyfikacji ubytku w planie | Gdy ubytek w planie uległ modyfikacji |
| `DERATE_WITHDRAWN` | Powiadomienie o wycofaniu ubytku z planu | Gdy ubytek został wycofany z planu |
| `CONTROL_MALFUNCTION_CREATED` | Powiadomienie o nowej niesprawności układu regulacji w planie | Gdy do planu została dodana nowa niesprawność układu regulacji |
| `CONTROL_MALFUNCTION_MODIFIED` | Powiadomienie o modyfikacji niesprawności układu regulacji w planie | Gdy niesprawność układu regulacji w planie uległa modyfikacji |
| `CONTROL_MALFUNCTIONE_WITHDRAWN` | Powiadomienie o wycofaniu niesprawności układu regulacji z planu | Gdy niesprawność układu regulacji została wycofana z planu |

<br> 

## Komunikat odpowiedzi, określającej status zgłoszenia
---
### Uczestnicy

| Rola | Podmiot |
|------|---------|
| Nadawca komunikatu | OSP (Operator Systemu Przesyłowego) |
| Odbiorca komunikatu | OSDp (Operator Systemu Dystrybucyjnego), Właściciel obiektu przyłączonego do sieci OSP |

### Charakterystyka komunikatu
Odpowiedź na zgłoszenie danych planistyczynych informuje o statusie zgłoszenia i ew. uwzględnieniu przekazywanych danych w planowaniu koordynacyjnym. Zawartość informacyjna odpowiedzi jest dostosowana do wszystkich komunikatów przekazujących zgłoszenia dotyczące danych planistycznych.

Odpowiedź ma analogiczną strukturę dla każdego rodzaju zgłoszenia:

* postoju
* ubytku
* niesprawności układu regulacji 
* harmonogramu dyspozycyjności
* pojemności użytkowej
* planu pracy
* poleceń ruchowych OSD
* salda wymiany

Komunikat odpowiedzi określa status (w szczególności przyjęcie bądź odrzucenie) danego rodzaju zgłoszenia.

Ponadto odpowiedź zawiera stempel czasowy zgłoszenia oraz wskazuje na to zgłoszenie poprzez jego identyfikator nadany przez nadawcę zgłoszenia. Dodatkowo podawany jest unikalny identyfikator nadany bez odbiorcę (OSP). 

Oprócz tego odpowiedź może zawierać jedną lub więcej wiadomości wskazujących na przyczynę odrzucenia. W przypadku potwierdzenia mogą również wystąpić wiadomości o charakterze ostrzegawczym lub informacyjnym. Na wiadomość składa się waga, kod, opis oraz pole z komunikatu zgłoszenia, do którego odnosi się wiadomość w odpowiedzi.


## Endpointy API
---
### GET `.../submissions/{serverMsgId}/status`
Pobranie statusu przetwarzania zgłoszenia.

| Parametr | Typ | Lokalizacja | Wymagany | Opis | Przykład |
|----------|-----|-------------|:--------:|------|----------|
| `serverMsgId` | uuid | path | tak | ID zgłoszenia nadane przez PSE | `550e8400-e29b-41d4-a716-446655440000` |

**operationId:** `getSubmissionProcessingStatus`  
**Tag:** Planning Data Submissions  

| Kod | Opis |
|-----|------|
| 200 | Status przetwarzania |
| 404 | Nie znaleziono zgłoszenia |
