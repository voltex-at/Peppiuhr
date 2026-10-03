# Peppiuhr v1.19.6 — wygląd aktualizacji

- Usunięto techniczne opisy i szczegóły diagnostyczne z ekranu aktualizacji zegara. Pozostają wersja, czytelny status i postęp instalacji.
- Aktywne przyciski powrotu i sprawdzania mają złote obramowanie. Instaluj otrzymuje je tylko wtedy, gdy aktualizacja jest dostępna. Przyciski zablokowane podczas operacji nie mają złotej ramki.
- Gdy oprogramowanie jest aktualne, numer wersji nie jest powtarzany.
- Panel web nie pokazuje kodów diagnostycznych ani opisu zainstalowanej wersji. Opis nowej wersji pozostaje widoczny przed instalacją. Log diagnostyczny przez USB pozostaje dostępny.
- Zachowano poprawkę PSRAM z v1.19.5 oraz potwierdzenie instalacji.

## Aktualizacja

Na v1.19.5 naciśnij Sprawdź aktualizacje, a następnie Instaluj i potwierdź. Nie odłączaj zasilania podczas instalacji. Jest to pierwsza próba pełnej instalacji OTA na zegarze użytkownika; sprawdzanie dostępności zostało już potwierdzone zdjęciem.

ZIP zawiera źródła, BIN i opis zmian bez grafik SD. Do OTA służy firmware.bin. Alternatywnie przez USB: firmware-merged.bin pod adres 0x0, ES3C28P ESP32-S3 16 MB, bez kasowania całej pamięci flash.
