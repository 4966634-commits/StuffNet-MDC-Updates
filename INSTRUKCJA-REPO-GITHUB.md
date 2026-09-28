# Utworzenie docelowego repo StuffNet-MDC-Updates

Faza 1 jest opublikowana **tymczasowo** w `StuffNet-Client/mdc-updates/` (token PAT ma dostep tylko do tego repo).

## Kroki (jednorazowo)

1. Utworz publiczne repo: https://github.com/new?name=StuffNet-MDC-Updates
2. Rozszerz fine-grained PAT (`github.token`):
   - Repository access: dodaj `StuffNet-MDC-Updates`
   - Permissions: **Contents** Read/Write, **Metadata** Read, **Releases** Read/Write
3. Z katalogu projektu MDC uruchom:

```powershell
powershell -ExecutionPolicy Bypass -File skrypty\publish-mdc-apk.ps1
```

Skrypt wrzuci pliki do `StuffNet-MDC-Updates` (manifest, APK w drzewie + Release).

## URL po migracji

- Manifest: `https://raw.githubusercontent.com/4966634-commits/StuffNet-MDC-Updates/main/latest.json`
- Release: `https://github.com/4966634-commits/StuffNet-MDC-Updates/releases`
