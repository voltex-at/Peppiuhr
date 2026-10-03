# Peppiuhr v1.19.5 — pamięć dla HTTPS

Diagnostyka v1.19.4 wykazała `T:8017 M:32512 F:0`: błąd konfiguracji TLS z powodu braku pamięci (`MBEDTLS_ERR_SSL_ALLOC_FAILED`, 0x7F00). Największy wolny blok miał 14324 bajty; bufor TLS ma 16384 bajty plus narzut.

- Pula LVGL 128 KiB przeniesiona z wewnętrznego RAM do PSRAM. Rozmiar puli i interfejs pozostają takie same.
- Przydział jest sprawdzany przed lv_init. Brak PSRAM prowadzi do dotychczasowej obsługi błędu startu, zamiast inicjalizacji LVGL z pustym wskaźnikiem.
- Błąd alokacji TLS jest teraz opisywany jako brak pamięci.
- Zachowano HTTPS, walidację certyfikatów, SHA-256, kontrolę modelu urządzenia i potwierdzenie aktualizacji.

## Wgranie

Ponieważ v1.19.4 nie ma dość RAM na OTA, wgraj przez USB `bin/firmware-merged.bin` pod adres `0x0`, ES3C28P ESP32-S3 16 MB. Bez kasowania całej pamięci flash. SD pozostaje bez zmian. Plik `bin/firmware.bin` służy wyłącznie do OTA.

Po wgraniu połącz zegar z routerem i naciśnij Sprawdź aktualizacje. Przy najnowszej wersji oczekiwany wynik to komunikat, że oprogramowanie jest aktualne. Jeżeli nadal wystąpi błąd, prześlij pełną diagnostykę z panelu web.

Przyczyna poprzedniego błędu jest potwierdzona kodem biblioteki. Działanie całego połączenia i późniejszej instalacji OTA wymaga jeszcze testu na fizycznym zegarze.

## Weryfikacja

Kompilacja zakończona sukcesem. Statyczne użycie RAM spadło z 203076 do 72012 bajtów (128 KiB minus 8 bajtów stanu puli). Test produkcyjnego przydziału puli z symulowanym sterownikiem potwierdził wybór PSRAM, obsługę braku pamięci, kontrolę rozmiaru i brak podwójnej alokacji.
