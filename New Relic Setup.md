# Monitoring_Setup

## To configure New Relic monitoring for your GKE cluster, the easiest and recommended way is using Helm. This gives you:

## GKE Cluster Monitoring

Node Monitoring
Pod Monitoring
Logs
Events
Kubernetes dashboards
APM (optional)
Alerts

## First create a New Relic account.

Open:

New Relic

Create:

Account
License Key

Then follow. 

## 1. Connect kubectl to GKE

```
gcloud container clusters get-credentials lottery-cluster \
--region asia-south1
```

## Verify:

```
kubectl get nodes
```


## 2. Install Helm (if missing)

Verify:

```
helm version
```

```
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```


## 3. Add New Relic Helm Repository

```
helm repo add newrelic https://helm-charts.newrelic.com

helm repo update

```


## 4. Create Namespace

```
kubectl create namespace newrelic
```


## 5. Install New Relic on GKE

Replace values:

```
YOUR_LICENSE_KEY
YOUR_CLUSTER_NAME
```
Example:

```
helm upgrade --install newrelic-bundle \
newrelic/nri-bundle \
--namespace=newrelic \
--set global.licenseKey=YOUR_LICENSE_KEY \
--set global.cluster=lottery-cluster \
--set kube-state-metrics.enabled=true \
--set prometheus.enabled=true \
--set logging.enabled=true
```


## 6. Verify Installation

Check pods:

```
kubectl get pods -n newrelic
```

Expected:
```
newrelic-infrastructure
newrelic-logging
newrelic-kube-events
newrelic-metadata
```


## 7. Open New Relic Dashboard

Open:

New Relic One

Navigate:

```
Infrastructure
→ Kubernetes
→ lottery-cluster
```

You should see:

CPU
Memory
Pods
Deployments
Nodes
Logs
Events



## 8. Enable Log Collection (Optional)
```
helm upgrade newrelic-bundle \
newrelic/nri-bundle \
--namespace=newrelic \
--reuse-values \
--set logging.enabled=true
```


## 9. Monitor Flask Application (Optional APM)

Inside your Flask container:
```
pip install newrelic
```

Generate config:

```
newrelic-admin generate-config \
YOUR_LICENSE_KEY \
newrelic.ini
```
Update Dockerfile:

```
CMD ["newrelic-admin","run-program","gunicorn","app:app"]
```

Now New Relic tracks:

Flask requests
Response time
Errors
Transactions


## 10. Uninstall

```
helm uninstall newrelic-bundle -n newrelic
kubectl delete namespace newrelic
```

Architecture:

<img width="287" height="238" alt="image" src="https://github.com/user-attachments/assets/e81a491a-3663-4f42-bf1c-73aea1437519" />



<img width="1882" height="801" alt="image" src="https://github.com/user-attachments/assets/15bf69aa-6471-4f38-9d65-ac3e80f4d56d" />

