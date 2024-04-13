# Mikroserwisy z Traefik Proxy

Projekt składa się z dwóch mikroserwisów: jednego napisanego w Flask służącego do pobierania danych o samochodach, oraz drugiego w Express.js do dodawania nowych danych o samochodach do bazy.

## Uruchamianie

Aby uruchomić projekt, upewnij się, że masz zainstalowany Docker i Docker Compose, a następnie wykonaj następujące kroki:

1. Klonowanie repozytorium:
``git clone <url-do-repozytorium>``
``cd <nazwa-folderu-repozytorium>``

3. Budowanie i uruchamianie kontenerów:
 ``docker-compose up --build``

To polecenie zbuduje obrazy dla obu aplikacji i uruchomi je wraz z Traefik jako reverse proxy.

3. Po uruchomieniu możesz odwiedzić dashboard Traefik:
``http://localhost:8080``
Dashboard pokaże Ci aktualne routery i serwisy.

## Zapytania do serwisu

### Flask App

- **Pobieranie wszystkich samochodów**
``curl http://localhost/api/flask/cars``

Możesz również użyć przeglądarki do wejścia na powyższy URL.

- **Pobieranie samochodów z danego rocznika (np. 2020)**
``curl http://localhost/api/flask/cars/2020``

Zmodyfikuj rok w URL, aby filtrować po innym roczniku.

### Express App

- **Pobieranie wszystkich samochodów**
``curl http://localhost/api/express/cars``

Ten URL można również otworzyć w przeglądarce.

- **Dodawanie nowego samochodu**
``curl -X POST http://localhost/api/express/addCar
-H "Content-Type: application/json"
-d '{"model":"Model S","year":2020,"details":"Electric Car"}'``

Zmodyfikuj JSON body (`-d`) w celu dodania innych danych o samochodach.

## Logi

Aby śledzić logi dla poszczególnych usług, możesz użyć:

- Dla Flask App:
``docker-compose logs flask-app``

- Dla Express App:
``docker-compose logs express-app``

## Sprzątanie

Po zakończeniu testów i pracy z aplikacją, możesz zatrzymać i usunąć kontenery oraz sieci tworzone przez `docker-compose` używając:

docker-compose down
