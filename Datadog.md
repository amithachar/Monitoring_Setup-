## Datadog GKE setup
<img width="1255" height="760" alt="image" src="https://github.com/user-attachments/assets/cb476315-3677-4a03-92ca-10152c498de2" />


<img width="1296" height="748" alt="image" src="https://github.com/user-attachments/assets/828c467e-a0cd-4c87-a372-52e05f16b24e" />


<img width="1346" height="797" alt="image" src="https://github.com/user-attachments/assets/fad25f5c-ee15-4524-a280-916052ac62cb" />


<img width="1332" height="480" alt="image" src="https://github.com/user-attachments/assets/0f4b9850-4cb5-4e64-8114-89894c2c86b0" />


# Dashboard

<img width="1703" height="816" alt="image" src="https://github.com/user-attachments/assets/2937bbb8-b89b-4858-8520-6b46142b87ba" />

<img width="1717" height="823" alt="image" src="https://github.com/user-attachments/assets/393f5e06-a598-4e6c-9395-aec33b377cef" />

<img width="1697" height="801" alt="image" src="https://github.com/user-attachments/assets/30069a48-fc60-417e-ad08-9bc82ea7e734" />

<img width="1705" height="813" alt="image" src="https://github.com/user-attachments/assets/165ef2f6-6b26-49f0-aab3-958cdff40a82" />


For a 4+ years SRE / DevOps interview, Datadog questions are usually scenario-based, not “what is Datadog”.

Here are the most commonly asked ones.

# 1. What is Datadog and why do we use it?

Expected answer:

Cloud monitoring and observability platform
Metrics
Logs
Traces (APM)
Alerts
Infrastructure monitoring
Kubernetes monitoring

# 2. Explain Datadog Architecture

Answer:

Application
↓
Datadog Agent
↓
Metrics / Logs / Traces
↓
Datadog Backend
↓
Dashboard / Alerts

Agent collects:

CPU
Memory
Disk
Logs
Network

# 3. Difference between Metrics, Logs, and Traces?

Type	Purpose
Metrics	Resource usage
Logs	Event history
Traces	Request flow

Example:

CPU=95%
↓
Check logs
↓
Trace API latency

# 4. How do you monitor Kubernetes in Datadog?

Answer:

Install Datadog Agent
↓
DaemonSet
↓
Cluster Agent
↓
Enable Kube-State-Metrics

Commands:

helm install datadog datadog/datadog

Monitor:

Nodes
Pods
Deployments
Services

# 5. One pod is continuously restarting. How do you troubleshoot in Datadog?

Answer:

Step 1:

Infrastructure
→ Kubernetes
→ Pod

Step 2:
Check:

CPU
Memory
Events
Logs

Step 3:

Container restart count

Step 4:
APM traces.

# 6. High CPU alert triggered. What do you do?

Answer:

Check:

CPU Metrics
↓
Container Metrics
↓
Pod Logs
↓
Deployment Rollout

Actions:

Scale pods
Tune requests/limits
Optimize code

# 7. Difference between Datadog Agent and Cluster Agent?

Agent	Cluster Agent
Runs per node	Runs once
Collects node data	Cluster-wide data

# 8. Explain Datadog APM

Answer:

Tracks:

Request
↓
Service
↓
DB
↓
External API

Shows:

Latency
Errors
Throughput

Python:

pip install ddtrace

# 9. How do you reduce Datadog cost?

Answer:

Sampling
Disable unused logs
Reduce retention
Tag filtering
Archive logs

# 10. What are Datadog monitors?

Types:

Metric monitor
Log monitor
APM monitor
Composite monitor
SLO monitor

Example:

CPU > 80%
for 10 min
→ Alert

# 11. Explain Datadog dashboard design

Answer:

Dashboard sections:

Availability
Latency
Errors
Traffic
Resources

# 12. What is SLO in Datadog?

Example:

Availability:
99.9%

Error budget:
0.1%

# 13. How do you monitor Jenkins in Datadog?

Answer:

Install integration.

Monitor:

Build duration
Queue time
Failures

# 14. Explain Datadog tagging strategy

Example:

env:prod
service:lottery
team:devops
cluster:gke

# 15. Difference: Prometheus vs Datadog

Prometheus	Datadog
Pull	Push
OSS	SaaS
Metrics	Full Observability

# 16. How do you alert Kubernetes pod crash?

Monitor:

kubernetes.containers.restarts

Condition:

> 3 in 10 mins

# 17. Explain Synthetic Monitoring

Answer:

Simulates:

Login
API
Website

# 18. Datadog Incident Response flow?
Alert
↓
Dashboard
↓
Logs
↓
Trace
↓
Root Cause
↓
Fix

# 19. Scenario: API latency suddenly increased

Answer:

Check:

APM
↓
Trace
↓
DB
↓
Logs
↓
Scaling

# 20. How do you monitor GKE using Datadog?

Answer:

GKE
↓
Datadog Agent
↓
Cluster Agent
↓
Dashboard
↓
Alerting
Tough interview question

# Q: Datadog shows CPU 95% but node CPU is 40%. Why?

Answer:

Container throttling
Incorrect limits
Short spikes
Aggregation differences
Datadog rollup intervals

These are strong 4+ years SRE interview Datadog questions.
