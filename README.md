# Projekt DevOps: FastAPI + PostgreSQL + Docker

Projekt realizowany w ramach przedmiotu **Nowatorski Projekt Indywidualny**.

## Technologie

* **Język**: Python
* **Framework**: FastAPI
* **Baza danych**: PostgreSQL 13
* **Konteneryzacja**: Docker & Docker Compose
* **Automatyzacja**: GitHub Actions

## Instrukcja uruchomienia (Lokalnie)

Wymagane jest posiadanie zainstalowanego Docker oraz Docker Compose.

1.  **Sklonuj repozytorium:**
    ```bash
    git clone https://github.com/dsw52673/nowatorski-projekt-indywidualny
    cd nowatorski-projekt-indywidualny
    ```

2.  **Uruchom środowisko:**
    ```bash
    docker-compose up --build
    ```

3.  **Dostęp do aplikacji:**
    * Aplikacja uruchomi się pod adresem: `http://localhost:8000`
    * Dokumentacja Swagger UI (do testowania endpointów): `http://localhost:8000/docs`

4.  **Zatrzymanie aplikacji:**
    Aby zatrzymać kontenery i usunąć utworzone zasoby:
    ```bash
    docker-compose down
    ```

## Testowanie API

Po uruchomieniu wejdź na stronę `http://localhost:8000/docs`. Możesz przetestować połączenie z bazą danych:
1.  Wybierz endpoint `POST /items/`.
2.  Kliknij **Try it out**.
3.  Wpisz przykładowe dane JSON, np. `{"name": "Testowy Element"}`.
4.  Kliknij **Execute** – jeśli otrzymasz kod 200, oznacza to poprawny zapis w bazie PostgreSQL.

## GitHub Actions (CI/CD)

W projekcie zdefiniowano dwa workflowy:
1.  **Pull Request Pipeline**: Uruchamia `flake8` (lint) oraz `pytest` (testy jednostkowe).
2.  **Main Branch Pipeline**: Po przejściu testów buduje obraz Docker i wypycha go do rejestru GitHub Container Registry (GHCR) przy użyciu *reusable workflow*.