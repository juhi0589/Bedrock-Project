Bedrock-Project
A modern WordPress starter project using Roots Bedrock and a Docker Compose-based monitoring stack (Prometheus, Node Exporter, Blackbox Exporter, Grafana), deployable on cloud VMs or local machines.

Project Structure
Bedrock - Modern WordPress
Composer-managed PHP dependencies

Secure, environment-driven configuration via .env and /config

Clean web root located at /web

WordPress core installed via Composer in /web/wp

Monitoring & Observability Stack
Docker Compose stack includes:

Prometheus (metrics database)

Node Exporter (system metrics)

Blackbox Exporter (HTTP probe)

Grafana (dashboards)

Dashboards are auto-provisioned and load automatically on Grafana startup

Quick Start
Clone and prepare the WordPress site:

bash
git clone https://github.com/juhi0589/Bedrock-Project.git
cd Bedrock-Project
composer install
cp .env.example .env
# Edit .env with your environment variables
Serve the /web directory using Nginx, Apache, or your preferred web server.

Deployment on Production Server (GCP VM / Linux Host)
Install Docker and Docker Compose

Clone repo and start monitoring stack:

bash
git clone https://github.com/juhi0589/Bedrock-Project.git
cd Bedrock-Project/monitoring
sudo docker compose up -d
Open firewall ports for monitoring dashboards:

Grafana (default port 3000)

Prometheus (default port 9090)

Access monitoring services:

Grafana: http://<server-ip>:3000

Prometheus: http://<server-ip>:9090

Example for your VM IP (34.6.110.173):

Grafana: http://34.6.110.173:3000

Prometheus: http://34.6.110.173:9090

CI/CD Caching Strategy and Deployment
Composer dependencies cached based on composer.lock hash

npm dependencies for Sage theme cached based on package.json hash

Cache keys refresh automatically on dependency changes

Deployment workflow:

Runs composer install during build to cache vendor/

Builds Sage theme npm assets and caches node_modules

Downloads cached artifacts and rsyncs code excluding sensitive files

Runs composer install on production server to install WordPress core (web/wp)

Fixes file/directory permissions and restarts PHP-FPM/nginx

Runs healthcheck endpoint to confirm deployment success

Rolls back on failure from backup copies

Managing Links and Plugins via WordPress Admin UI
Login to the WordPress admin panel at /wp/wp-login.php (e.g., http://34.6.110.173/wp/wp-login.php).

Managing Links:

Navigate to Appearance > Menus to create or edit site navigation

Edit Pages and Posts to update internal/external links

Managing Plugins:

Visit Plugins > Installed Plugins

Activate, deactivate, update, or remove plugins

Add new plugins via the Add New button from the admin UI

Ensure compatibility and disable any plugins causing issues
