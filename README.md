Bedrock-Project
A modern WordPress starter project using Roots Bedrock and a Docker Compose-based monitoring stack (Prometheus, Node Exporter, Blackbox Exporter, Grafana), deployable on cloud VMs or local machines.

📦 Project Structure
Bedrock: Modern WordPress with secure, environment-driven configuration (via .env and /config).

Monitoring: Automated Docker Compose stack for infrastructure and HTTP health, with auto-provisioned Grafana dashboards.

Part 1: WordPress Bedrock App
Features:

Composer-managed dependencies

Clean config and secure file structure

Modern web root at /web

Quick start:

text
git clone https://github.com/juhi0589/Bedrock-Project.git
cd Bedrock-Project
composer install
cp .env.example .env  # Fill in your info
Serve the /web directory using Nginx, Apache, or your preferred web server.

Part 2: Monitoring & Observability (GCP VM/Cloud)
Stack:

Prometheus (metrics DB)

Node Exporter (system metrics)

Blackbox Exporter (HTTP probe)

Grafana (dashboards)

Setup Guide (on your GCP VM or any Linux host):

Install Docker and Docker Compose:

text
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install -y docker-ce docker-compose-plugin
Clone and enter the monitoring folder:

text
git clone https://github.com/juhi0589/Bedrock-Project.git
cd Bedrock-Project/monitoring
Start all services with Docker Compose (requires sudo unless your user is in the docker group):

text
sudo docker compose up -d
Access the services (from anywhere if GCP firewall is open):

Grafana: http://<VM-IP>:3000

Prometheus: http://<VM-IP>:9090

Default Grafana login: admin / admin (change this after first login).

🔥 Note on Firewall/Cloud Access
On GCP, firewall rules must allow inbound TCP on 3000 (Grafana) and 9090 (Prometheus).

See the Google Cloud Console "VPC network > Firewall" for port settings.

Example: Grafana at http://34.6.110.173:3000 and Prometheus at http://34.6.110.173:9090.

💡 Tips
Use sudo with all Docker/Docker Compose commands unless your user is explicitly added to the docker group.

To avoid sudo each time: sudo usermod -aG docker $USER then log out and back in.

📊 Dashboards & Provisioning
Dashboards (JSON) and provisioning YAMLs are under monitoring/dashboards/ and monitoring/provisioning/

Metrics, Node, Blackbox, and HTTP health are preconfigured

All dashboards auto-load in Grafana at first launch
