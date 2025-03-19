<<<<<<< HEAD
# self-healing-kubernetes-clusters
Automate self-healing of applications by monitoring container health and restarting failing pods.
=======
# Self-Healing Kubernetes Clusters

This project implements automated self-healing capabilities for Kubernetes clusters using Prometheus, Alertmanager, and KEDA (Kubernetes Event-driven Autoscaling).

## Features

- Container health monitoring using Prometheus and Grafana
- Automated pod restarts based on health metrics
- Dynamic workload scaling using KEDA
- Alert management and notification system

## Prerequisites

- Kubernetes cluster (v1.20+)
- Helm v3
- kubectl
- Prometheus Operator
- Grafana
- KEDA

## Project Structure

```
.
├── README.md
├── kubernetes/
│   ├── prometheus/
│   │   ├── prometheus-values.yaml
│   │   └── alertmanager-values.yaml
│   ├── grafana/
│   │   └── grafana-values.yaml
│   └── keda/
│       └── keda-values.yaml
├── examples/
│   └── sample-app/
│       ├── deployment.yaml
│       └── service.yaml
└── monitoring/
    └── dashboards/
        └── pod-health.json
```

## Installation

1. Install Prometheus and Alertmanager:
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install prometheus prometheus-community/kube-prometheus-stack -f kubernetes/prometheus/prometheus-values.yaml -n monitoring
```

2. Install KEDA:
```bash
helm repo add kedacore https://kedacore.github.io/charts
helm install keda kedacore/keda -f kubernetes/keda/keda-values.yaml -n keda
```

3. Deploy sample application:
```bash
kubectl apply -f examples/sample-app/
```

## Monitoring

Access the monitoring dashboards:
- Prometheus: http://localhost:9090
- Grafana: http://localhost:3000 (default credentials: admin/admin)

## Self-Healing Configuration

The system is configured to:
- Monitor pod health metrics (CPU, memory, readiness, liveness)
- Automatically restart pods that fail health checks
- Scale workloads based on custom metrics using KEDA
- Send alerts for critical issues

## Contributing

Feel free to submit issues and enhancement requests! 
>>>>>>> 5ab5551 (Initial commit)
