# Peppiuhr v1.19.7 — czytelny postęp aktualizacji

- Pasek na ekranie zegara ma wysokość 20 px zamiast 8 px, ciemne nieprzezroczyste tło, zaokrąglone rogi i złote wypełnienie z delikatnym gradientem.
- Nad paskiem znajduje się duży procent rzeczywistego postępu pobierania i zapisu firmware.
- Pasek i procent są widoczne podczas instalacji, weryfikacji i restartu. W pozostałych stanach pozostają ukryte.
- Zachowano złote obramowania aktywnych przycisków, brak opisów diagnostycznych oraz poprawkę PSRAM.

## Aktualizacja

Sprawdź aktualizacje → Instaluj → Potwierdź. Nie odłączaj zasilania podczas instalacji. Nowy wygląd pojawi się po restarcie; pobieranie v1.19.7 obsługuje jeszcze interfejs poprzedniej wersji.

ZIP zawiera źródła, BIN i opis zmian, bez grafik SD. Do OTA służy firmware.bin. Alternatywnie USB: firmware-merged.bin pod 0x0, ES3C28P ESP32-S3 16 MB, bez erase-flash.
