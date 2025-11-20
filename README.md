📡 IoT Monitoring System using Prometheus & SNMP

This project implements a real-time IoT Device Monitoring System using Prometheus, SNMP Exporter, and Docker Compose. The system collects metrics from IoT devices via SNMP, converts them using SNMP Exporter, and visualizes them using Prometheus.

🚀 Features:

✔ Real-time IoT device monitoring

✔ SNMP-based metrics collection (CPU, memory, bandwidth, uptime, etc.)

✔ Prometheus time-series database

✔ Docker-based deployment (easy setup)

✔ Customizable prometheus.yml and snmp.yml

✔ Scalable to multiple IoT devices

🏗 Project Architecture IoT Device → SNMP Agent → SNMP Exporter → Prometheus → Dashboard / Alerts

📂 Repository Structure

📁 IOT-MONITORING/ │── docker-compose.yml │── prometheus.yml │── snmp.yml └── README.md

⚙️ Technologies Used Tool Purpose Prometheus Metrics scraping and storage SNMP Exporter Converts SNMP data → Prometheus format Docker & Docker Compose Container orchestration SNMP Protocol Device-level metrics collection 📌 Setup Instructions

Follow these steps to run the monitoring system on your machine:

1️⃣ Install Required Tools

Before running the project, ensure you have:

Docker

Docker Compose

(Optional) Grafana for dashboards

2️⃣ Clone the Repository git clone https://github.com//IOT-MONITORING.git cd IOT-MONITORING

3️⃣ Configure SNMP Targets

Open snmp.yml and set:

IoT device IP

SNMP community

Required OIDs for metrics

Example:

modules: if_mib: walk: - 1.3.6.1.2.1.1 version: 2

4️⃣ Configure Prometheus Targets

In prometheus.yml, define your SNMP exporter as a scrape target:

scrape_configs:

job_name: 'snmp' static_configs:
targets:
'snmp-exporter:9116'
5️⃣ Start the System

Run:

docker-compose up -d

This will start:

Prometheus

SNMP Exporter

6️⃣ Access Dashboards ▶ Prometheus UI http://localhost:9090

▶ SNMP Exporter Metrics http://localhost:9116/metrics

📊 Monitoring & Alerts

You can run PromQL queries such as:

up node_cpu_seconds_total ifInOctets ifOutOctets

You may also integrate Grafana for better visualization.

🧪 Testing the Setup

Verify Prometheus is scraping metrics

Check SNMP Exporter logs

Confirm the IoT device is reachable via SNMP

Use tools like snmpwalk for validation

Example:

snmpwalk -v2c -c public

📈 Future Enhancements

Add Grafana dashboards

Add alerting rules in alert.rules.yml

Anomaly detection using ML

Support for SNMP v3 authentication

🤝 Contributing

Contributions are welcome! Feel free to fork the repository and submit a Pull Request.

🙌 Acknowledgments

Prometheus Team

SNMP Exporter contributors

Docker Community
