# Peppiuhr v1.19.3 — łączenie Wi-Fi

- Stara próba połączenia jest przerywana bezpośrednio w sterowniku ESP-IDF, także gdy nie została jeszcze zestawiona. Po 500 ms rozpoczyna się próba z zapisanymi danymi.
- Kontrolowany wynik rozpoczęcia połączenia, limit próby 30 sekund i kolejna próba po 60 sekundach. Ponowny zapis tych samych danych przy braku połączenia również uruchamia nową próbę.
- Panel pokazuje rzeczywisty wynik połączenia: połączono z adresem IP, błąd uwierzytelnienia, brak sieci, przekroczony czas lub błąd rozpoczęcia próby. Kod przyczyny z modułu Wi-Fi ułatwia diagnozę; błąd uwierzytelnienia nie musi oznaczać wyłącznie złego hasła.
- Osobny komunikat o trwającym skanowaniu sieci.
- Różowe przyciski zapisu zastąpiono złotym gradientem jak w ikonach.

Źródło problemu znalezione w używanej bibliotece: funkcja rozłączenia Arduino może zakończyć się bez przerwania próby, jeżeli stan nie jest jeszcze „connected”. Poprawka usuwa tę kolizję; nie potwierdzono, że była jedyną przyczyną problemu z routerem użytkownika.

Testy logiki ponownego łączenia (symulowany sterownik), formularza mobilnego, rzeczywistych komunikatów z API i koloru przycisku przeszły. Firmware skompilowany. Połączenie z fizycznym routerem wymaga sprawdzenia na zegarze.

## Wgranie

Jeżeli zegar ma internet: aktualizacja OTA do v1.19.3. Jeśli nadal nie może się połączyć, użyj USB: `bin/firmware-merged.bin`, adres `0x0`, ES3C28P ESP32-S3 16 MB. Nie wykonuj erase-flash, jeśli chcesz zachować konfigurację. Do OTA służy `bin/firmware.bin`.

Po wgraniu zamknij i ponownie otwórz captive portal. Wybierz sieć, wpisz hasło, naciśnij zapis i poczekaj około 30 sekund. Jeśli połączenie się nie powiedzie, prześlij komunikat z kodem wyświetlony pod przyciskiem — nie wysyłaj hasła.
