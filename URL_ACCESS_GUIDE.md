# Complete URL Access Guide

## ✓ ACCESSIBLE URLs - Open in Browser

### Docker Container Services (Host Machine)
These are running as Docker containers on your local machine:

| Service | URL | Username | Password | Notes |
|---------|-----|----------|----------|-------|
| **SonarQube** | http://localhost:9000 | admin | admin | Code quality analysis |
| **JFrog Artifactory** | http://localhost:8083 | mukeshjpr432 | DoHare@1991 | Docker registry |
| **Jenkins** | http://localhost:8082 | admin | 857a566964964703a4cdf9597467c01d | CI/CD pipeline |

### Kubernetes Services (K8s NodePort)
These are running in Kubernetes with NodePort exposure:

| Service | URL | Username | Password | Notes |
|---------|-----|----------|----------|-------|
| **Krayin CRM App** | http://localhost:30080 | admin@example.com | admin123 | Main application |
| **Krayin Admin Panel** | http://localhost:30080/admin/login | admin@example.com | admin123 | Admin dashboard |
| **Prometheus** | http://localhost:30090 | - | - | Metrics collection |
| **Grafana** | http://localhost:30300 | admin | admin | Dashboard visualization |
| **Loki** | http://localhost:30100 | - | - | Log aggregation API |

---

## 🚀 How to Access Each URL

### 1. Krayin CRM Application (Main App)
```
URL: http://localhost:30080
Purpose: Customer Relationship Management System
Login:
  Email: admin@example.com
  Password: admin123
```

### 2. Krayin CRM Admin Panel (Admin Dashboard)
```
URL: http://localhost:30080/admin/login
Purpose: Admin management interface
Login:
  Email: admin@example.com
  Password: admin123
```

### 3. Jenkins (CI/CD Pipeline)
```
URL: http://localhost:8082
Purpose: Continuous Integration/Deployment
Initial Setup Password: 857a566964964703a4cdf9597467c01d
Steps:
  1. Go to http://localhost:8082
  2. Paste the initial password above
  3. Complete setup wizard
  4. Create new pipeline job pointing to Jenkinsfile
```

### 4. SonarQube (Code Quality Analysis)
```
URL: http://localhost:9000
Purpose: PHP code quality and security analysis
Login:
  Username: admin
  Password: admin
```

### 5. JFrog Artifactory (Docker Registry)
```
URL: http://localhost:8083
Purpose: Docker image storage and management
Login:
  Username: mukeshjpr432
  Password: DoHare@1991
Image: trial8mlq0s.jfrog.io/docker-local/krayin-crm:latest
```

### 6. Prometheus (Metrics Collection)
```
URL: http://localhost:30090
Purpose: Monitoring metrics collection and queries
Features:
  - View metrics
  - Create alerts
  - Check targets status
No authentication required
```

### 7. Grafana (Dashboard & Visualization)
```
URL: http://localhost:30300
Purpose: Visualize metrics and create dashboards
Login:
  Username: admin
  Password: admin
Datasources:
  - Prometheus (metrics)
  - Loki (logs)
```

### 8. Loki (Log Aggregation)
```
URL: http://localhost:30100
Purpose: Log collection and aggregation API
Method: REST API (used by Grafana)
No authentication required
Endpoint: http://localhost:30100/loki/api/v1/
```

---

## ✅ Service Status

### Docker Containers
```
✓ sonarqube (Port 9000)              - Code quality analysis
✓ artifactory (Port 8083)            - Docker artifact repository  
✓ jenkins (Port 8082)                - CI/CD automation
✓ postgres-artifactory (Port 5432)   - Database
✓ crm-app (Port 8080)                - Alternate CRM access
```

### Kubernetes Pods
```
✓ krayin-crm-* (2 replicas)          - Running on NodePort 30080
✓ prometheus-* (Port 30090)          - Running in monitoring namespace
✓ grafana-* (Port 30300)             - Running in monitoring namespace
✓ loki-* (Port 30100)                - Running in logging namespace
✓ promtail-* (DaemonSet)             - Log collector running
```

---

## 📋 Quick Reference Table

| What | URL | When to Use |
|------|-----|------------|
| **Access Main App** | http://localhost:30080 | Use the CRM application |
| **Admin Login** | http://localhost:30080/admin/login | Manage system settings |
| **Setup CI/CD** | http://localhost:8082 | Configure Jenkins pipeline |
| **Code Quality** | http://localhost:9000 | Review SonarQube analysis |
| **View Artifacts** | http://localhost:8083 | Check Docker images in registry |
| **Monitor System** | http://localhost:30090 | Check application metrics |
| **View Dashboards** | http://localhost:30300 | Visualize metrics and logs |
| **Check Logs** | http://localhost:30100 | Access log aggregation API |

---

## 🔧 Troubleshooting

### If a URL is not accessible:

1. **Check if services are running:**
   ```bash
   docker ps                    # Check Docker containers
   kubectl get pods -A          # Check Kubernetes pods
   ```

2. **Check service status:**
   ```bash
   docker ps | grep SERVICE_NAME
   kubectl get svc -A
   ```

3. **Restart service:**
   ```bash
   docker restart SERVICE_NAME
   kubectl rollout restart deployment/SERVICE_NAME -n NAMESPACE
   ```

4. **View logs:**
   ```bash
   docker logs CONTAINER_ID
   kubectl logs POD_NAME -n NAMESPACE
   ```

5. **Check ports:**
   ```bash
   netstat -ano | findstr :PORT_NUMBER    # Windows
   lsof -i :PORT_NUMBER                   # Mac/Linux
   ```

---

## 📚 Common Tasks

### Access CRM Admin Panel
1. Open: http://localhost:30080/admin/login
2. Enter credentials: admin@example.com / admin123
3. Navigate dashboard

### Monitor Application in Real-time
1. Open Grafana: http://localhost:30300 (admin/admin)
2. Add Prometheus datasource
3. Create dashboard with metrics

### View Application Logs
1. Open Grafana: http://localhost:30300
2. Add Loki datasource: http://loki.logging:3100
3. Query logs in Logs section

### Deploy Code Changes via Jenkins
1. Open Jenkins: http://localhost:8082
2. Create Pipeline job with GitHub repo
3. Configure Jenkinsfile path
4. Click "Build Now" to trigger 11-stage pipeline

### Check Code Quality
1. Open SonarQube: http://localhost:9000 (admin/admin)
2. Create project: laravel-crm
3. View analysis results after Jenkins build

---

## 🎯 Next Steps

1. **Access Application**: http://localhost:30080
2. **Setup Jenkins**: http://localhost:8082 (complete wizard)
3. **Create Pipeline**: Point to Jenkinsfile from GitHub
4. **Configure SonarQube**: Add credentials in Jenkins
5. **Setup Monitoring**: Create dashboards in Grafana
6. **Trigger Pipeline**: Build Now in Jenkins

---

All URLs are ready! Open them in your browser now.
