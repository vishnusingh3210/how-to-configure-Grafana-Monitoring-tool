# how-to-configure-Grafana-Monitoring-tool
# Grafana Monitoring Tool

This repository provides a complete guide to installing, configuring, and using
**Grafana** for monitoring servers, systems, and applications.

Grafana is an open-source visualization and analytics platform commonly used with
**Prometheus** for metrics monitoring.

---

## 📌 Prerequisites

### System Requirements
- Linux (Ubuntu 20.04 / 22.04 recommended)
- Minimum 2 GB RAM
- Internet access
- Root or sudo privileges

### Required Software
- Grafana
- Prometheus
- Node Exporter (for system metrics)

---

## 🧰 Components Overview

| Component | Purpose |
|--------|--------|
| Grafana | Visualization & dashboards |
| Prometheus | Metrics collection |
| Node Exporter | System metrics exporter |

---

## 🚀 Step-by-Step Installation

### 1️⃣ Update System
```bash
sudo apt update && sudo apt upgrade -y

2️⃣ Install Grafana
sudo apt install -y apt-transport-https software-properties-common wget
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee /etc/apt/sources.list.d/grafana.list

sudo apt update
sudo apt install -y grafana


Start Grafana:

sudo systemctl start grafana-server
sudo systemctl enable grafana-server


Access Grafana:

http://<server-ip>:3000


Default credentials:

username: admin
password: admin

3️⃣ Install Prometheus
sudo useradd --no-create-home --shell /bin/false prometheus
wget https://github.com/prometheus/prometheus/releases/latest/download/prometheus-linux-amd64.tar.gz
tar xvf prometheus-linux-amd64.tar.gz
cd prometheus-*


Move binaries:

sudo cp prometheus /usr/local/bin/
sudo cp promtool /usr/local/bin/

4️⃣ Install Node Exporter
wget https://github.com/prometheus/node_exporter/releases/latest/download/node_exporter-linux-amd64.tar.gz
tar xvf node_exporter-linux-amd64.tar.gz
sudo cp node_exporter-*/node_exporter /usr/local/bin/


Run Node Exporter:

node_exporter

🔗 Connect Prometheus to Grafana

Login to Grafana

Go to Settings → Data Sources

Click Add data source

Select Prometheus

URL:

http://localhost:9090


Click Save & Test

📊 Import Dashboards

Grafana → Dashboards

Click Import

Use dashboard ID:

1860


Select Prometheus as data source

🚨 Alerts & Monitoring

Create alerts from dashboard panels

Configure notification channels (Email, Slack, Webhook)

Monitor CPU, memory, disk, and network usage

🛠 Troubleshooting
Grafana Service Status
sudo systemctl status grafana-server

Prometheus Status
curl http://localhost:9090

Node Exporter Status
curl http://localhost:9100/metrics

📎 Useful Commands
sudo systemctl restart grafana-server
sudo systemctl stop grafana-server
sudo systemctl start grafana-server

📚 References

https://grafana.com/docs/

https://prometheus.io/docs/
