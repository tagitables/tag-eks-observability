# Kubernetes Monitoring and Alerting

A namespace-isolated Kubernetes monitoring demonstration using Prometheus, Alertmanager, and a Python webhook receiver on AWS EKS.

## Architecture

Prometheus
    |
    | Evaluates alerting rules
    v
Alertmanager
    |
    | Routes firing alerts
    v
Kubernetes ClusterIP Service
    |
    | HTTP POST /alert
    v
Python Webhook Receiver
    |
    | Structured JSON
    v
Container Logs

## Components

- Prometheus: Metric collection and alert evaluation
- Alertmanager: Alert grouping, routing and notification delivery
- Python Webhook: Receives and logs alert notifications
- Kubernetes: Namespace-isolated Deployments, Services and ConfigMaps

## Environment

- Platform: Amazon EKS
- Namespace: tag-coaching20-prom
- Helm release: tag-coaching20-prom
- Prometheus Helm chart: prometheus-community/prometheus

## Verification

Successfully demonstrated:

- Prometheus alert rule evaluation
- Coaching20TestAlert entering FIRING state
- Alertmanager receiving the active alert
- Webhook notification routing
- HTTP POST /alert returning 200 OK
- JSON alert payloads appearing in container logs

## Browser Interfaces

Prometheus:

http://localhost:9090/alerts

Alertmanager:

http://localhost:9093/#/alerts

These interfaces require local Kubernetes port-forwarding.

## Security and Isolation

All deployed resources are restricted to the dedicated monitoring namespace.

The demonstration avoids modifying shared cluster-wide resources, including those belonging to other users.

## Notes

Coaching20TestAlert is a synthetic demonstration alert, not a real infrastructure failure indicator.
