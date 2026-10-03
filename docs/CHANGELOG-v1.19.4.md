# Peppiuhr v1.19.4 — diagnostyka aktualizacji

- Ekran zegara i panel web pokazują etap błędu, numer połączenia w łańcuchu przekierowań, status HTTP, kody ESP/TLS, flagi certyfikatu, wolną pamięć wewnętrzną/największy blok i czas UTC jako znacznik Unix.
- Osobne komunikaty dla DNS, daty certyfikatu, TLS, HTTP i niedozwolonego przekierowania. Diagnostyka nie zawiera haseł ani podpisanych adresów pobierania.
- Limit oczekiwania połączenia zwiększony z 10 do 20 sekund.
- Wielokropek i pauzę na ekranie aktualizacji zastąpiono znakami obsługiwanymi przez wbudowaną czcionkę. Znika prostokąt po słowie Updates.
- Zachowano sprawdzanie certyfikatów HTTPS, dozwolonych serwerów, sumy SHA-256 i potwierdzenie instalacji.

## Co wiadomo

Zdjęcie v1.19.3 potwierdza połączenie zegara z routerem. Publiczny manifest GitHub i jego dwa przekierowania działają podczas sprawdzenia z komputera. Dotychczasowy ogólny błąd nie pozwala ustalić przyczyny na ESP32. Ta wersja jest diagnostyczna; nie deklaruje rozwiązania nieustalonego błędu połączenia.

## Wgranie i sprawdzenie

Jeśli OTA nie działa, wgraj przez USB `bin/firmware-merged.bin` pod adres `0x0` (ES3C28P, ESP32-S3, 16 MB). Nie kasuj całej pamięci flash. Pliki SD nie są potrzebne. Do OTA służy wyłącznie `bin/firmware.bin`.

Połącz zegar z routerem, ustaw prawdziwą datę i godzinę, naciśnij Sprawdź aktualizacje. Jeżeli wystąpi błąd, prześlij pełny komunikat wraz z kodami, najlepiej z panelu web. Nie przesyłaj hasła Wi-Fi.

Kompilacja i testy programowe nie zastępują sprawdzenia połączenia na fizycznym urządzeniu.
