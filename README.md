📡 IoT Monitoring System using Prometheus & SNMP

This project implements a real-time IoT Monitoring System using Prometheus, SNMP Exporter, and Docker Compose.
The system collects SNMP metrics from IoT devices, converts them via the SNMP Exporter, and visualizes them in Prometheus.

🚀 Features

✔ Real-time IoT device monitoring

✔ SNMP-based metrics collection (CPU, memory, bandwidth, uptime, etc.)

✔ Prometheus time-series storage

✔ Docker-based deployment (simple & portable)

✔ Customizable prometheus.yml and snmp.yml

✔ Supports multiple IoT devices

🏗 Project Architecture
IoT Device → SNMP Agent → SNMP Exporter → Prometheus → Dashboard / Alerts

📂 Repository Structure
IOT-MONITORING/
│── docker-compose.yml
│── prometheus.yml
│── snmp.yml
└── README.md

⚙️ Technologies Used
Tool	Purpose
Prometheus	Metrics scraping & storage
SNMP Exporter	Converts SNMP metrics → Prometheus format
Docker Compose	Container orchestration
SNMP Protocol	Device-level metrics collection
📌 Setup Instructions

Follow these steps to run the monitoring system:

1️⃣ Install Required Tools

Make sure you have installed:

Docker

Docker Compose

(Optional) Grafana for dashboards

2️⃣ Clone the Repository
git clone https://github.com/gowda084/iot_monitoring.git
cd iot_monitoring

3️⃣ Configure SNMP Targets

Edit snmp.yml:

Set IoT device IP, SNMP community, and OIDs.

Example:

modules:
  if_mib:
    walk:
      - 1.3.6.1.2.1.1
    version: 2

4️⃣ Configure Prometheus Targets

Inside prometheus.yml, define SNMP exporter as a scrape target:

scrape_configs:
  - job_name: 'snmp'
    static_configs:
      - targets: ['snmp-exporter:9116']

5️⃣ Start the System
docker-compose up -d


This launches:

Prometheus

SNMP Exporter

6️⃣ Access Dashboards
Service	URL
Prometheus UI	http://localhost:9090

SNMP Exporter	http://localhost:9116/metrics
📊 Monitoring & Alerts

Example PromQL queries:

up

node_cpu_seconds_total

ifInOctets

ifOutOctets

Integrate Grafana for advanced dashboards.

🧪 Testing the Setup

Verify SNMP is working using:

snmpwalk -v2c -c public <DEVICE_IP>


Check:

Prometheus scrape status

SNMP Exporter logs

Device SNMP connectivity

📈 Future Enhancements

Add Grafana dashboards

Add alerting rules (alert.rules.yml)

Anomaly detection using ML

SNMP v3 authentication support




SNMP Exporter Contributors

Docker Community
