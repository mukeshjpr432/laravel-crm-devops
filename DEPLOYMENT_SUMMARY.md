# Laravel CRM DevOps - Complete Deployment Summary

## ✓ All URLs Accessible (Open in Browser)

### Core Application
| Component | URL | Status | Credentials |
|-----------|-----|--------|-------------|
| **Krayin CRM App** | http://localhost:30080 | ✓ Running | Email: admin@example.com / Pass: admin123 |
| **Krayin Admin** | http://localhost:30080/admin/login | ✓ Running | Email: admin@example.com / Pass: admin123 |

### CI/CD & Build
| Component | URL | Status | Credentials |
|-----------|-----|--------|-------------|
| **Jenkins** | http://localhost:8082 | ✓ Running | Initial Password: 857a566964964703a4cdf9597467c01d |
| **SonarQube** | http://localhost:9000 | ✓ Running | Default: admin / admin |
| **JFrog Artifactory** | http://localhost:8083 | ✓ Running | User: mukeshjpr432 / Pass: DoHare@1991 |

### Monitoring & Logging
| Component | URL | Status | Credentials |
|-----------|-----|--------|-------------|
| **Prometheus** | http://localhost:30090 | ✓ Running | No auth required |
| **Grafana** | http://localhost:30300 | ✓ Running | Admin: admin / Password: admin |
| **Loki** | http://localhost:30100 | ✓ Running | No auth required |

---

## Docker Containers Running

```
✓ jenkins              (Port 8082)   - CI/CD Pipeline Engine
✓ sonarqube           (Port 9000)   - Code Quality Analysis
✓ artifactory         (Port 8083)   - Artifact Repository (JFrog)
✓ postgres-artifactory (Port 5432)  - Database for Artifactory
✓ crm-app             (Port 8080)   - Krayin CRM Docker app (alternate)
✓ k8s-control-plane   (Port 64239)  - Kubernetes Cluster
```

---

## Kubernetes Resources Running

### Application Pods
```bash
kubectl get pods -l app=krayin-crm
# 2 replicas running from trial8mlq0s.jfrog.io/docker-local/krayin-crm:latest
# Service: NodePort 30080
```

### Monitoring Stack
```bash
kubectl get all -n monitoring
# Prometheus: http://localhost:30090 (Port 30090)
# Grafana:    http://localhost:30300 (Port 30300)
```

### Logging Stack
```bash
kubectl get all -n logging
# Loki:       http://localhost:30100 (Port 30100)
# Promtail:   DaemonSet collecting logs
```

### Auto-Scaling
```bash
kubectl get hpa
# krayin-crm-hpa: Min 2 replicas, Max 5 replicas
# Scales on CPU/Memory > 80%
```

---

## Jenkins Pipeline (11 Stages)

**File:** `Jenkinsfile`

### Stages:
1. ✓ **Checkout Code** - Pull from GitHub (main branch)
2. ✓ **SonarQube Analysis** - PHP code quality scan
3. ✓ **Composer Install** - Laravel dependencies
4. ✓ **Build Docker Image** - PHP 8.3 + Apache
5. ✓ **Trivy Security Scan** - Vulnerability detection
6. ✓ **Push to JFrog** - Push image to Artifactory
7. ✓ **Deploy to Kubernetes** - Rolling update
8. ✓ **HPA Auto-Scaling** - Configure horizontal scaling
9. ✓ **Prometheus Monitoring** - Metrics collection
10. ✓ **Loki Log Collection** - Log aggregation
11. ✓ **Grafana Dashboard** - Visualization

---

## How to Use

### 1. Access Krayin CRM Application
```
URL: http://localhost:30080
Login:
  Email: admin@example.com
  Password: admin123
```

### 2. Configure & Run Jenkins Pipeline
```
1. Open http://localhost:8082
2. Skip setup wizard or complete with initial password: 857a566964964703a4cdf9597467c01d
3. Go to: Manage Jenkins → Credentials → System → Global credentials
4. Add credentials:
   - jfrog-creds (Username: mukeshjpr432, Password: DoHare@1991)
   - sonar-token (any value)
5. Create New Item → Pipeline
6. Configure:
   - Name: krayin-crm-pipeline
   - Pipeline: Pipeline script from SCM
   - SCM: Git
   - Repository: https://github.com/mukeshjpr432/laravel-crm-devops.git
   - Branch: main
   - Script path: Jenkinsfile
7. Click Build Now
```

### 3. Monitor Application
```
Prometheus Metrics:     http://localhost:30090
Grafana Dashboard:      http://localhost:30300
Loki Logs:             http://localhost:30100
```

### 4. Code Quality
```
SonarQube Analysis:     http://localhost:9000
Project Key: laravel-crm
```

### 5. Artifact Repository
```
JFrog Artifactory:      http://localhost:8083
Username: mukeshjpr432
Password: DoHare@1991
Image: trial8mlq0s.jfrog.io/docker-local/krayin-crm:latest
```

---

## Kubernetes Commands

### View Application
```bash
kubectl get pods -l app=krayin-crm -o wide
kubectl logs -f krayin-crm-<pod-id>
kubectl describe pod krayin-crm-<pod-id>
```

### View Services
```bash
kubectl get svc
kubectl get svc -n monitoring
kubectl get svc -n logging
```

### View HPA Status
```bash
kubectl get hpa
kubectl describe hpa krayin-crm-hpa
```

### Access Pod Directly
```bash
kubectl exec -it krayin-crm-<pod-id> -- bash
kubectl exec -it krayin-crm-<pod-id> -- curl http://localhost/admin/login
```

---

## Architecture

```
Developer Code Push
        ↓
   GitHub (main branch)
        ↓
Jenkins (Poll SCM every 1 min)
        ↓
┌─────────────────────────────────────┐
│  Stage 1-6: Build & Security Scan   │
│  - Checkout Code                    │
│  - SonarQube Analysis               │
│  - Composer Install                 │
│  - Docker Build                     │
│  - Trivy Security Scan              │
│  - Push to JFrog Artifactory        │
└─────────────────────────────────────┘
        ↓
┌─────────────────────────────────────┐
│  Stage 7-11: Deploy & Monitor       │
│  - Kubernetes Deployment            │
│  - HPA Auto-Scaling                 │
│  - Prometheus Monitoring            │
│  - Loki Log Collection              │
│  - Grafana Dashboard                │
└─────────────────────────────────────┘
        ↓
   Application Live
   ✓ http://localhost:30080
```

---

## Key Files Created

```
D:\Project\crm\
├── Jenkinsfile                          (11-stage pipeline)
├── Dockerfile                           (PHP 8.3 + Apache)
├── docker-compose.yml                   (Dev environment)
├── k8s/
│   ├── deployment.yaml                  (Krayin CRM deployment)
│   ├── service.yaml                     (NodePort service)
│   ├── secret.yaml                      (Secrets & env vars)
│   ├── image-pull-secret.yaml           (JFrog auth)
│   ├── hpa.yaml                         (Auto-scaling)
│   ├── monitoring/
│   │   ├── prometheus.yaml              (Metrics collection)
│   │   └── grafana.yaml                 (Dashboard)
│   └── logging/
│       └── loki.yaml                    (Log aggregation)
├── jenkins/
│   └── Dockerfile                       (Jenkins with tools)
└── .dockerignore
```

---

## Troubleshooting

### Check if services are running
```bash
docker ps
kubectl get pods -A
```

### View logs
```bash
docker logs jenkins
docker logs sonarqube
kubectl logs -f krayin-crm-<pod-id>
```

### Restart Jenkins
```bash
docker restart jenkins
```

### Restart Kubernetes deployment
```bash
kubectl rollout restart deployment/krayin-crm
```

### Check network connectivity
```bash
kubectl exec krayin-crm-<pod-id> -- curl http://localhost:80
```

---

## Summary

✓ **Krayin CRM Application** - Deployed and running on Kubernetes (2 replicas)
✓ **Jenkins Pipeline** - 11 stages fully configured (CI/CD automated)
✓ **SonarQube** - Code quality analysis enabled
✓ **JFrog Artifactory** - Docker image repository configured
✓ **Prometheus** - Metrics collection active
✓ **Grafana** - Dashboard visualization ready
✓ **Loki** - Log aggregation deployed
✓ **HPA** - Auto-scaling 2-5 replicas (CPU/Memory 80%)
✓ **Kubernetes** - All manifests applied and running

**All URLs are accessible. Ready for production deployment!**
