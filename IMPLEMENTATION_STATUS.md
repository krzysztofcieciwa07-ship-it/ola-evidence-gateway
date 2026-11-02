# OLA Evidence Gateway — status implementacji

Migawka: **2026-11-02** · repozytorium jest publicznym **forkiem** `krzys167-crypto/ola-evidence-gateway`.

## Co można potwierdzić

Na domyślnej gałęzi `main` znajdują się `README.md`, ustawienia `.devcontainer/` i `.vscode/`. **Nie ma tu kodu uruchamialnego serwera Evidence Gateway, testów serwera ani manifestów wdrożenia.**

Obszerne README opisuje **model i wymagania** zbierania dowodów. Ten opis nie jest wykonywalnym API, dowodem działania ani potwierdzeniem produkcyjnej integralności.

`OLA` posiada implementację endpointów dowodowych w swoim własnym repozytorium, ale jej obecność nie oznacza, że **ten fork** jest działającą instancją Gateway.

## Stan

- Specyfikacja: `SOURCE_PRESENT` (README).
- Osobny serwer: `NOT_IMPLEMENTED_IN_THIS_REPO`.
- Niezależne testy end-to-end: `NOT_VERIFIED`.
- Publiczne wdrożenie: `UNKNOWN`.
- Systemowa gotowość 10/10: **`BLOCKED`**.

## Dalsza decyzja — bez automatycznego nadpisywania

- **Opcja A:** utrzymać repozytorium jako dokumentację/specyfikację i wskazać `OLA/app` jako obecny kod.
- **Opcja B:** utworzyć odrębny serwis dopiero po rozdzieleniu odpowiedzialności, schematów API, trwałości, auth, tenant isolation i testów.
- Sprawdzić i ręcznie poprawić metadane GitHub: pole homepage obecnie wskazuje niepowiązaną stronę pogodową. Nie przypisywać jej do OLA.
- Nie uruchamiać automatycznie CI/deploy bez kodu, konfiguracji i poprawnej polityki sekretów.

[Katalog wszystkich repozytoriów OLA](https://github.com/krzysztofcieciwa07-ship-it/OLA/blob/main/docs/REPOSITORY_CATALOG.md) — stanie się dostępny na `main` po przeglądzie PR.

**Zasada:** dokumentacja ≠ artefakt serwera ≠ działające API ≠ zweryfikowana produkcja.
