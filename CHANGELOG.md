# Changelog

W tym pliku znajdują się informacje o nowych, zmienionych lub poprawionych definicjach w specyfikacjach API. Dotyczy to również zmian w dokumentacji

Format logu zmian zgodnie z [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]


## [1.0.0] - 2026-07-31

### Dodano

### Zmieniono
- Zmiana wymagalności dla TimeSeriesContinuous, TimeSeriesPoints, TimeSeriesData

### Naprawiono

### Dokumentacja
- Zaktualizowane zapisy o danych planistycznych odnoszących się do MWE z wieloma składowymi, po ustaleniach z PSE
- Rozszerzenie opisu dotyczącego ograniczenia zdolności regulacji mocy biernej
- Doprecyzowanie zakresu niesprawności regulacji.
- Aktualizacja mapowalności w zależności od rodzaju obiektu i danych
- Uzupełnienie opisów dotyczących szczegółowego udostępniania niedostępności i niesprawności
- Rozdział główny: 
    - Rozszerzenie i korekta zapisów w tabeli parametrów zgłoszeń
    - Rozszerzenie zapisów dotyczących kompletności zgłoszeń i sposobu usuwania opcjonalnych danych grafikowych
    - Poprawa opisu dotyczącego możliwych wartości 0/1 dla danych typu znacznik.
    - Wskazanie dokładności początków i końców okresów
    - Doprecyzowanie udostępniania danych planistycznych w kontekście zadanego obiektu oraz okresu
    - Doprecyzowanie biznesowego zakresu komunikatu polecenia ruchowego OSD
    - Korekty zakresu rozdzielczości
    - Uzupełnienie dotyczące możliwego ograniczenia zakresu dopuszczalnych wartości określonych w specyfikacji API przez reguły biznesowe
- Korekty czytelności zapisów

## [1.0.0-beta] - 2026-05-11

### Dodano
- Nowe endpointy SSE dla notyfikacji o zmianach statusów zgłoszeń i zmianach niedostępności w aktualnym planie 
- Nowe endpointy REST do pobierania informacji o pojedynczych niedostępnościach
- Indywidualne typy dla zgłoszeń niedostępności (postoje, ubytki, niesprawności układów regulacji)
- Obsługa ograniczeń zdolności regulacji mocy biernej

### Zmieniono
- Usunięto asynchroniczne API

### Naprawiono

### Dokumentacja
- Zaktualizowano dokumentację dotyczącą nowych endpointów

## [1.0.0-alpha] - 2025-12-18

Wersja inicjalna

[Unreleased]: https://github.com/Polskie-Sieci-Elektroenergetyczne/planning-api/compare/v1.0.0-beta...HEAD
[1.0.0]: https://github.com/Polskie-Sieci-Elektroenergetyczne/planning-api/releases/tag/v1.0.0
[1.0.0-beta]: https://github.com/Polskie-Sieci-Elektroenergetyczne/planning-api/releases/tag/v1.0.0-beta
[1.0.0-alpha]: https://github.com/Polskie-Sieci-Elektroenergetyczne/planning-api/releases/tag/v1.0.0-alpha