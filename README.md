Kubernetes Application Observability & Alerting Platform
Project Overview
This project implements a Kubernetes-based application observability and alerting platform using Prometheus, Grafana, Alertmanager, and the Prometheus Operator.

A containerized Python Flask application is deployed inside Kubernetes with multiple replicas. The application exposes Prometheus-compatible metrics through the /metrics endpoint.

Prometheus discovers and scrapes the application using a Kubernetes ServiceMonitor. Grafana visualizes application and Kubernetes resource metrics using PromQL queries.

PrometheusRule resources are used to detect application failures and resource utilization issues. The project also demonstrates Kubernetes self-healing by intentionally deleting application pods and observing Kubernetes automatically create replacement pods.

Project Objectives
The main objectives of this project are:

Deploy a containerized application on Kubernetes
Expose application metrics using Prometheus client instrumentation
Configure Prometheus ServiceMonitor for automatic metric discovery
Collect application metrics with Prometheus
Query metrics using PromQL
Create a professional Grafana monitoring dashboard
Monitor HTTP request traffic
Monitor application availability
Monitor CPU utilization
Monitor memory utilization
Monitor network traffic
Configure PrometheusRule-based alerts
Test application failure scenarios
Demonstrate Kubernetes self-healing
Visualize application recovery using Grafana
Architecture
                     Kubernetes Cluster
                            |
            +---------------+---------------+
            |                               |
      monitoring-app                    monitoring
            |                               |
    +---------------+              +----------------+
    | Flask App     |              | Prometheus     |
    | 3 Replicas    |              | Grafana        |
    +---------------+              | Alertmanager   |
            |                      +----------------+
            |
    +---------------+
    | Kubernetes    |
    | Service       |
    +---------------+
            |
            v
    +---------------+
    | ServiceMonitor|
    +---------------+
            |
            v
       Prometheus
            |
          PromQL
            |
            v
         Grafana
            |
          Alerts
            |
            v
      Alertmanager
Monitoring Flow
User | v Flask Application | +------ /metrics | v Kubernetes Service | v ServiceMonitor | v Prometheus | +------ PromQL | v Grafana | v Monitoring Dashboard

Technologies Used
Technology	Purpose
Kubernetes	Container orchestration
Docker	Containerization
Docker Desktop	Local Kubernetes environment
Helm	Kubernetes package management
Prometheus	Metrics collection and monitoring
Prometheus Operator	Kubernetes-native Prometheus management
Grafana	Metrics visualization and dashboards
Alertmanager	Alert handling and routing
PromQL	Prometheus query language
ServiceMonitor	Kubernetes service discovery for Prometheus
PrometheusRule	Prometheus alert configuration
Python	Application development
Flask	Web application framework
Git	Version control
GitHub	Source code hosting
Project Structure
kubernetes-prometheus-grafana-monitoring/ │ ├── README.md │ ├── application/ │ ├── namespace.yaml │ ├── deployment.yaml │ ├── service.yaml │ ├── app.py │ ├── Dockerfile │ └── requirements.txt │ ├── monitoring/ │ ├── servicemonitor.yaml │ └── prometheusrule.yaml │ ├── dashboards/ │ └── kubernetes-app-dashboard.json │ ├── screenshots/ │ ├── 01-project-structure.png │ ├── 02-cluster-running.png │ ├── 03-monitoring-pods.png │ ├── 04-application-running.png │ ├── 05-application-metrics.png │ ├── 06-prometheus-target-up.png │ ├── 07-promql-query.png │ ├── 08-grafana-dashboard.png │ ├── 09-alert-firing.png │ ├── 10-application-recovered.png │ ├── 11-self-healing.png │ └── 12-recovery-dashboard.png │ └── docs/ └── architecture.md

Key Monitoring Capabilities
The project monitors:

Application Availability HTTP Request Rate Total HTTP Requests HTTP Request Duration CPU Utilization Memory Utilization Network Traffic Pod Availability Application Health

Key Learnings
Through this project, I demonstrated practical knowledge of:

Kubernetes monitoring
Prometheus architecture
PromQL
Grafana dashboard creation
ServiceMonitor configuration
PrometheusRule configuration
Alerting
Application observability
Kubernetes self-healing
Resource monitoring
Metrics-based troubleshooting
Useful Kubernetes Commands
Check application pods
kubectl get pods -n monitoring-app

Check application deployment
kubectl get deployment -n monitoring-app

Check application service
kubectl get svc -n monitoring-app

Check ServiceMonitor
kubectl get servicemonitor -n monitoring

Check PrometheusRule
kubectl get prometheusrules -n monitoring

Check monitoring pods
kubectl get pods -n monitoring

Check Helm release
helm list -n monitoring

Scale application
kubectl scale deployment monitoring-demo-app --replicas=3 -n monitoring-app

Watch application pods
kubectl get pods -n monitoring-app -w

Project Results
The completed project demonstrates an end-to-end Kubernetes observability workflow:

Application | v Docker Container | v Kubernetes Deployment | v Kubernetes Service | v ServiceMonitor | v Prometheus | +------ PromQL | v Grafana | +------ Dashboards | +------ Visualization | v PrometheusRule | v Alertmanager

The project also demonstrates:

Failure ↓ Detection ↓ Alert ↓ Recovery ↓ Self-Healing ↓ Monitoring

Future Improvements
Potential future improvements include:

Add Alertmanager notification integration
Add persistent Grafana dashboards
Implement Kubernetes HPA using metrics
Add Ingress monitoring
Add MongoDB monitoring
Deploy the project to Azure Kubernetes Service (AKS)
Integrate CI/CD using Azure DevOps
Add TLS and authentication
Add application latency SLO/SLI monitoring
These future improvements align with the roadmap in the project source.

Author
JangamReddy05 Kubernetes | Docker | Helm | Prometheus | Grafana | Azure DevOps | Cloud & DevOps
