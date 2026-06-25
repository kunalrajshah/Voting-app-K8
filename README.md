# Kubernetes Voting Application

## Project Overview

This project demonstrates deploying a multi-tier voting application on Kubernetes.

Users can vote between Cats and Dogs through a web interface. Votes are stored in Redis, processed by a Worker service, saved into PostgreSQL, and displayed through a Result application.

---

## Architecture

```text
Vote App
   |
   v
 Redis
   |
   v
 Worker
   |
   v
PostgreSQL
   |
   v
Result App
```

### Components

* Vote Application (Frontend)
* Redis (Temporary Queue)
* Worker (Processes Votes)
* PostgreSQL (Database)
* Result Application (Displays Results)

---

## Kubernetes Resources Used

### Pods

* vote
* redis
* worker
* db
* result

### Services

| Service | Type      | Port  |
| ------- | --------- | ----- |
| vote    | NodePort  | 30001 |
| result  | NodePort  | 30002 |
| redis   | ClusterIP | 6379  |
| db      | ClusterIP | 5432  |

---

## Prerequisites

* Docker Desktop
* Kubernetes Enabled
* kubectl
* Git

Verify Kubernetes:

```bash
kubectl cluster-info
kubectl get nodes
```

---

## Deployment Steps

### Deploy All Resources

```bash
kubectl apply -f .
```

### Verify Pods

```bash
kubectl get pods
```

Expected:

```text
vote     Running
redis    Running
worker   Running
db       Running
result   Running
```

### Verify Services

```bash
kubectl get svc
```

Expected:

```text
vote     NodePort
result   NodePort
redis    ClusterIP
db       ClusterIP
```

---

## Access Application

### Vote Application

```text
http://localhost:30001
```

### Result Application

```text
http://localhost:30002
```

---

## Troubleshooting

### Check Pod Logs

```bash
kubectl logs vote
kubectl logs result
kubectl logs worker
kubectl logs db
kubectl logs redis
```

### Check Services

```bash
kubectl get svc
```

### Check Endpoints

```bash
kubectl get endpoints
```

### Describe Resources

```bash
kubectl describe pod <pod-name>
kubectl describe svc <service-name>
```

---

## Learning Outcomes

* Kubernetes Pods
* Services (ClusterIP and NodePort)
* Service Discovery
* Pod-to-Pod Communication
* Redis Integration
* PostgreSQL Integration
* Kubernetes Troubleshooting
* Containerized Application Deployment

---

## Author

Kunal Kumar

DevOps & Cloud Enthusiast
AWS | Docker | Kubernetes | Terraform

```
```

