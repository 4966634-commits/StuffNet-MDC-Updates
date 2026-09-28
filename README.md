# StuffNet-MDC-Updates

Oficjalne aktualizacje APK **StuffNet Mobile Data Cleaner v3** (OTA).

Aplikacja sprawdza plik [`latest.json`](latest.json) (raw URL na branch `main`).

**Docelowy URL (repo `StuffNet-MDC-Updates`):**
```
https://raw.githubusercontent.com/4966634-commits/StuffNet-MDC-Updates/main/latest.json
```

**Tymczasowy URL (do czasu utworzenia osobnego repo — token PAT ma dostep tylko do `StuffNet-Client`):**
```
https://raw.githubusercontent.com/4966634-commits/StuffNet-Client/main/mdc-updates/latest.json
```

## Publikacja nowej wersji (maintainer)

Z katalogu projektu MDC:

```powershell
powershell -ExecutionPolicy Bypass -File skrypty\publish-mdc-apk.ps1
```

Opcjonalnie wskaz konkretny APK:

```powershell
powershell -ExecutionPolicy Bypass -File skrypty\publish-mdc-apk.ps1 -ApkPath "release\StuffNet-MDC-11.3.62-v3.apk"
```

Skrypt:

1. Liczy SHA256 APK
2. Aktualizuje `latest.json`
3. Kopiuje APK do tego repo
4. Commit + push na `main`
5. Tworzy/aktualizuje GitHub Release (tag `v{versionName}`)
6. Podmienia asset Release
7. Podmienia plik APK w **drzewie** repo (lista plikow na GitHub)

## Token GitHub

Potrzebny PAT z uprawnieniami `repo` (zapis). Lokalizacja (pierwsza istniejaca):

- `G:\CURSORWORKSPACE\sekrety\StuffNet-Client\github.token`
- `DOKUMENTACJA\sekrety\github-token.txt` (projekt Fabric)

## Struktura manifestu

| Pole | Opis |
|------|------|
| `versionCode` | Porownanie z `BuildConfig.VERSION_CODE` w aplikacji |
| `versionName` | Etykieta wersji (np. `11.3.61-v3`) |
| `apkFileName` | Nazwa pliku APK |
| `downloadUrl` | Bezposredni URL pobrania (Release asset) |
| `sha256` | Hex lowercase — weryfikacja po pobraniu |
| `minVersionCode` | Opcjonalne minimum (pomin aktualizacje jesli starsze) |
| `releaseNotes` | Krotki opis po polsku |

Repo publiczne: https://github.com/4966634-commits/StuffNet-MDC-Updates
