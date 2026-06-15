# Monitoring_Setup-
Monitoring_Setup  for all montioring tools

# GKE Monitoring with New Relic

Configuring New Relic monitoring for your Google Kubernetes Engine (GKE) cluster using Helm provides a comprehensive visibility stack out of the box.

## Features Covered
* **GKE Cluster Monitoring:** Overall health metrics of the cluster.
* **Node & Pod Monitoring:** Granular CPU, memory, and disk usage tracking.
* **Log & Event Collection:** Real-time Kubernetes events and stdout/stderr application logs.
* **Dashboards & Alerts:** Pre-built Kubernetes dashboards and customizable alert policies.
* **Application Performance Monitoring (APM):** Optional tracing for hosted applications (e.g., Flask).

---

## Prerequisites

Before beginning, ensure you have:
1. A New Relic account. If you don't have one, sign up at [New Relic](https://newrelic.com).
2. Generated your **New Relic License Key**.
3. Google Cloud SDK (`gcloud`) and `kubectl` installed locally.

---

## Deployment Steps

### 1. Connect kubectl to GKE
Authenticate your local terminal with your target cluster:
```bash
gcloud container clusters get-credentials lottery-cluster --region asia-south1
