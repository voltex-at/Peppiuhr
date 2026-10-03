# Peppiuhr v1.19.1

- Ikona aktualizacji (okrężne strzałki) zamiast napisu OTA w ustawieniach.
- Ekran aktualizacji wykorzystuje tło odtwarzacza dla bieżącego trybu Countdown Mode, także warianty Krampus/Nikolaus. Półprzezroczysty panel zapewnia czytelność tekstu.
- Poprawiona strzałka powrotu w lewym dolnym rogu: używa znaku dostępnego w dołączonej czcionce zamiast brakującego symbolu.
- Nagłówek „Aktualizacja” po polsku, „Update” po niemiecku i angielsku.
- Oznaczenie przejścia między wersjami używa znaku obecnego w czcionce.

## Instalacja

Z wersji 1.19.0: połącz zegar z domowym Wi-Fi z internetem, ustaw prawidłowy czas, otwórz OTA i naciśnij Sprawdź / Prüfen. Potwierdź instalację v1.19.1. Nie odłączaj zasilania podczas zapisu.

Alternatywnie USB: wgraj `bin/firmware-merged.bin` pod adres `0x0` (tylko ES3C28P ESP32-S3 16 MB). Plik `bin/firmware.bin` przeznaczony jest do OTA; nie używaj obrazu merged do OTA. Nie wykonuj erase-flash, jeśli chcesz zachować ustawienia. Grafiki SD pozostają bez zmian.

Kompilacja PlatformIO zakończona powodzeniem. Podgląd rzeczywistego LVGL sprawdzony dla DE/PL/EN, z kontrolą dostępności obu ikon. Test na fizycznym zegarze pozostaje po stronie użytkownika.

Paczka zawiera kod źródłowy, BIN-y, metadane i opis zmian; bez ponownego zestawu grafik SD i podglądów.
