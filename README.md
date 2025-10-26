Bedrock-Project
A modern, production-ready WordPress solution powered by Roots Bedrock, Composer, and a plug-and-play observability stack (Prometheus, Node Exporter, Blackbox Exporter, Grafana) via Docker Compose.

📦 Project Structure
Bedrock: Modern WordPress project boilerplate with secure, environment-based configuration and Composer integration.

Monitoring: Complete local observability setup; auto-provisioned dashboards for system health and app endpoints.

Part 1: WordPress Bedrock Setup
Features
Secure and modern folder structure for WordPress.

Composer-based management of plugins, themes, and WordPress core.

Environmental configuration using .env files and /config overrides.

Web root served from /web.

Getting Started
Clone & Enter Repo

text
git clone https://github.com/juhi0589/Bedrock-Project.git
cd Bedrock-Project
Install Dependencies

text
composer install
Environment Setup

Copy .env.example to .env.

Edit .env with your database/access credentials and WordPress URLs.

Document Root

Bedrock serves the site from the /web folder (e.g., for Apache/Nginx, set webroot to [project]/web).

Further Configuration

Edit config/application.php and view Bedrock documentation for more.

Part 2: Monitoring & Observability Stack
Everything you need to monitor your application stack out-of-the-box!

Stack Components
Prometheus: Main metrics collector and time series database.

Node Exporter: System and hardware metrics (CPU, RAM, disk).

Blackbox Exporter: Probe HTTP endpoint health.

Grafana: Dashboard visualizations, auto-provisioned.

Quickstart
Go to Monitoring Directory

text
cd monitoring
Start Monitoring Services

text
docker compose up -d
Access the Web UIs

Prometheus: http://localhost:9090

Grafana: http://localhost:3000 (admin / admin)

Dashboards & Configuration
Pre-provisioned dashboards for:

Node system metrics (CPU, memory)

Application HTTP health (probe_success)

All dashboards are auto-loaded in Grafana under Dashboards > Manage.

To check or edit configuration:

Prometheus: monitoring/prometheus.yml

Blackbox Exporter: monitoring/blackbox.yml

Grafana dashboards: monitoring/dashboards/

Grafana provisioning: monitoring/provisioning/dashboards/dashboard.yml (dashboard loader),
monitoring/provisioning/datasources/prometheus.yml (optional, datasource loader)

🙋 FAQ & Help
Where do I run composer? In the root directory after cloning.

Where do I start monitoring? In the /monitoring folder.

Is data source auto-provisioned? Yes, if provisioning/datasources/prometheus.yml is present.

What about secrets? Never commit your filled .env or any real secrets to Git!
