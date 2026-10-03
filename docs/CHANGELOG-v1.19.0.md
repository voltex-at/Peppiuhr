# Peppiuhr v1.19.0 — OTA

- Aktualizacja z GitHub Releases na żądanie: sprawdzenie wersji, opis zmian i osobne potwierdzenie instalacji.
- Przycisk OTA w ustawieniach zegara oraz sekcja aktualizacji w panelu web; języki DE/PL/EN.
- HTTPS z weryfikacją certyfikatów, kontrola modelu ES3C28P/ESP32-S3 16 MB, rozmiaru, wersji i SHA-256.
- Zapis do nieaktywnej partycji. Nowy obraz wybierany dopiero po poprawnej weryfikacji.
- Zatwierdzanie obrazu po inicjalizacji interfejsu i 10 sekundach pracy pętli głównej. Bootloader obsługuje rollback po restarcie niezatwierdzonej aplikacji. To nie jest pełny test wszystkich urządzeń peryferyjnych.
- Muzyka zatrzymywana przed instalacją, zapisy konfiguracji i transfery plików blokowane podczas OTA.
- Bez automatycznego sprawdzania i instalowania nowych wersji. Dane użytkownika i pliki SD nie są częścią aktualizacji OTA.

## Pierwsza instalacja

Dotychczasowy firmware bez OTA wymaga wgrania przez USB. `firmware-merged.bin` jest kompletnym obrazem do adresu `0x0` dla ES3C28P/ESP32-S3 z 16 MB flash. Nie używaj go jako pliku OTA.

Przykład po zainstalowaniu esptool 5.1.0 (zastąp PORT):

```sh
python -m esptool --chip esp32s3 --port PORT write-flash 0x0 firmware-merged.bin
```

Nie używaj `erase-flash`, jeżeli chcesz zachować konfigurację. Przed pierwszym przejściem na nowy firmware warto zapisać ustawienia. Zgodność zachowania danych wymaga tej samej tabeli partycji.

## Kolejne aktualizacje

Połącz zegar z domowym Wi-Fi z dostępem do internetu i ustaw poprawny czas. Sam hotspot zegara nie dostarcza internetu. Otwórz OTA w ustawieniach lub panelu web, wybierz „Sprawdź aktualizacje”, przeczytaj opis, a następnie potwierdź instalację. Nie odłączaj zasilania podczas zapisu. Po restarcie zegar pracuje na nowej wersji. Bieżąca v1.19.0 zgłosi brak nowszej wersji, dopóki nie opublikujemy kolejnego wydania.

`firmware.bin` to obraz aplikacji dla OTA. `ota.json` zawiera dokładny rozmiar, SHA-256 i adres tego pliku. SHA-256 wykrywa uszkodzenie pliku; nie jest podpisem cyfrowym. Zaufanie opiera się na HTTPS i kontroli konta/repozytorium GitHub.

## Sprawdzenie

Kompilacja PlatformIO dla ES3C28P zakończona powodzeniem. Testy logiki dat i zasad OTA wykonywane na komputerze. Panel web testowany z atrapami API. Fizyczne pobranie, restart i rollback na zegarze wymagają sprawdzenia na sprzęcie; nie zostały wykonane zdalnie.

Paczka zawiera źródła, BIN-y, metadane aktualizacji i ten opis. Nie zawiera ponownie katalogów grafik na SD ani podglądów.
