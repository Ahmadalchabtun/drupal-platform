# Drupal Platform

Dit is een schaalbaar en veilig platform voor Drupal-websites, draaiend in Docker.

## Hoe te starten
1. Clone deze repository: `git clone https://github.com/Ahmadalchabtun/drupal-platform.git`
2. Ga naar de map: `cd drupal-platform`
3. Start de containers: `docker-compose up -d`
4. Ga naar `http://192.168.120.16:80` om de Drupal-site te zien.

## Services
- Drupal: De website
- MySQL: Database
- Nginx: Webserver

## Beveiliging
- **Trivy**: Gebruikt om container-images te scannen op kwetsbaarheden.
- **Falco**: Bewaakt verdacht gedrag in containers tijdens runtime.
  - **Test**: Een shell gestart in de Drupal-container (`docker exec -it drupal-platform_drupal_1 bash`). Falco detecteerde dit en logde het in `/var/log/syslog` met de melding: "A shell was spawned in a container with an attached terminal".
## CI/CD
- **GitHub Actions**: Automatische pipeline die bij elke push naar de `master`-branch de Docker-containers bouwt, start, test of de Drupal-site bereikbaar is, en de containers weer stopt.
  - Workflow-bestand: `.github/workflows/ci.yml`
  - Test: Controleert of de site bereikbaar is via `http://localhost` met een `curl`-test.
