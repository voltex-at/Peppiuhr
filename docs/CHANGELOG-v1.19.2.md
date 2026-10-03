# Peppiuhr v1.19.2 — zapis Wi-Fi

- Osobny przycisk „Zapisz Wi-Fi i połącz” / „WLAN speichern und verbinden” / „Save Wi-Fi and connect” bezpośrednio pod hasłem.
- Osobna obsługa zapisu Wi-Fi: nie wymaga poprawnego wypełnienia pól daty urodzin ani innych sekcji formularza, nie zmienia jasności i ustawień trybu.
- Komunikat o zapisywaniu, powodzeniu lub błędzie przy przycisku. Hasło pozostaje w polu po błędzie zapisu.
- Wyłączona autokorekta, automatyczne wielkie litery i sprawdzanie pisowni hasła. Przycisk Pokaż/Ukryj zachowuje kursor. Wybór sieci otwartej wyłącza pole hasła, wybór sieci zabezpieczonej je włącza.
- Zachowano autoryzację, kontrolę CSRF oraz walidację po stronie urządzenia.

Testy mobilnego panelu: wybór sieci, znaki specjalne w haśle, odświeżanie bez utraty tekstu, niezależny zapis Wi-Fi, błędne/krótkie hasło, sieć otwarta i języki DE/PL/EN. Kompilacja zakończona powodzeniem. API symulowane; konkretnego okna captive portal iOS ani połączenia z routerem nie testowano fizycznie.

## Wgranie

Jeżeli zegar ma internet: OTA / ikona aktualizacji → Sprawdź → potwierdź v1.19.2.
Jeżeli błąd formularza uniemożliwia podłączenie zegara do internetu: wgraj przez USB `bin/firmware-merged.bin` pod adres `0x0` (ES3C28P ESP32-S3, 16 MB). Nie wykonuj erase-flash, jeśli chcesz zachować ustawienia. Do OTA służy wyłącznie `bin/firmware.bin`.

Po aktualizacji zamknij i ponownie otwórz okno konfiguracji Wi-Fi w telefonie, aby wczytać nowy formularz. Nie odłączaj zasilania podczas instalacji. Pliki SD nie wymagają zmian.

Paczka zawiera źródła, BIN-y i opis zmian. Bez ponownego kompletu grafik SD.
