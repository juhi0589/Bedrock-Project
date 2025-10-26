Bedrock-Project
A modern WordPress starter project using Roots Bedrock and a Docker Compose-based monitoring stack (Prometheus, Node Exporter, Blackbox Exporter, Grafana), deployable on cloud VMs or local machines.

Project Structure
Bedrock - Modern WordPress
Composer-managed PHP dependencies

Secure, environment-driven configuration with .env and /config

Clean web root at /web

WordPress core installed via Composer in /web/wp

Monitoring & Observability
Docker Compose stack includes:

Prometheus (metrics DB)

Node Exporter (system metrics)

Blackbox Exporter (HTTP probe)

Grafana (dashboards)

Dashboards auto-provision and load at Grafana startup

Quick Start
Clone and prepare the WordPress site:

bash
git clone https://github.com/juhi0589/Bedrock-Project.git
cd Bedrock-Project
composer install
cp .env.example .env
# Edit .env with your environment variables
Serve the /web directory using Nginx, Apache, or your web server.

Deployment on Production Server (GCP VM / Linux Host)
Install Docker and Docker Compose

Clone the repo and start monitoring stack:

bash
git clone https://github.com/juhi0589/Bedrock-Project.git
cd Bedrock-Project/monitoring
sudo docker compose up -d
Open firewall ports for monitoring dashboards:

Grafana (default at port 3000)

Prometheus (default at port 9090)

Access services:

Grafana: http://<server-ip>:3000

Prometheus: http://<server-ip>:9090

Example for your VM IP 34.6.110.173:

Grafana: http://34.6.110.173:3000

Prometheus: http://34.6.110.173:9090

CI/CD Caching Strategy and Deployment
Composer caches dependencies based on the composer.lock hash.

npm caches for Sage theme based on the package.json hash.

Cache keys refresh automatically on dependency changes.

Deploy workflows:

Run composer install in build job

Cache and upload artifacts (vendor/ and web/app/themes/sage/public/)

Rsync code excluding sensitive files

Run composer install on production server to install WordPress core (web/wp)

Set correct permissions

Reload PHP-FPM and nginx

Run healthcheck endpoint in CI to confirm deployment success

Rollback on failure using backups

Managing Links and Plugins in WordPress Admin UI
Login at /wp/wp-login.php (e.g., http://34.6.110.173/wp/wp-login.php).

Links:

Go to Appearance > Menus to edit site navigation.

Edit Pages and Posts for internal and external links.

Plugins:

Go to Plugins > Installed Plugins.

Activate/deactivate/update plugins.

Add new plugins via Add New button.

Ensure compatibility and deactivate any causing errors.
