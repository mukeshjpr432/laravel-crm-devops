# 🎯 QUICK START - COPY & PASTE URLs

## Open These in Your Browser NOW ⬇️

```
http://localhost:30080                          ← KRAYIN CRM APP
http://localhost:30080/admin/login              ← ADMIN LOGIN
http://localhost:8082                           ← JENKINS
http://localhost:9000                           ← SONARQUBE
http://localhost:8083                           ← ARTIFACTORY
http://localhost:30090                          ← PROMETHEUS
http://localhost:30300                          ← GRAFANA
http://localhost:30100                          ← LOKI
```

---

## 🔐 LOGIN CREDENTIALS

| Service | Username | Password |
|---------|----------|----------|
| **Krayin CRM** | admin@example.com | admin123 |
| **Jenkins** | (create after setup) | 857a566964703a4cdf9597467c01d (initial) |
| **SonarQube** | admin | admin |
| **Grafana** | admin | admin |
| **JFrog Artifactory** | mukeshjpr432 | DoHare@1991 |
| **Prometheus** | N/A | N/A |
| **Loki** | N/A | N/A |

---

## ✅ WHAT TO CHECK IN EACH URL

### 1. Krayin CRM (http://localhost:30080)
- [ ] Page loads
- [ ] Redirects to /admin/login
- [ ] CRM logo appears
- [ ] Login form visible

### 2. Admin Login (http://localhost:30080/admin/login)
- [ ] Login page displays
- [ ] Email input field present
- [ ] Password input field present
- [ ] Sign In button visible
- [ ] Login with admin@example.com / admin123

### 3. Jenkins (http://localhost:8082)
- [ ] Jenkins page loads
- [ ] Dashboard or Setup Wizard appears
- [ ] Initial password prompt (first time)
- [ ] Paste: 857a566964703a4cdf9597467c01d

### 4. SonarQube (http://localhost:9000)
- [ ] SonarQube loads
- [ ] Login page or dashboard
- [ ] Login: admin / admin
- [ ] Can create projects

### 5. Artifactory (http://localhost:8083)
- [ ] Artifactory loads
- [ ] Login page visible
- [ ] Login: mukeshjpr432 / DoHare@1991
- [ ] Can browse repositories

### 6. Prometheus (http://localhost:30090)
- [ ] Prometheus interface loads
- [ ] "Graph" tab visible
- [ ] "Alerts" tab visible
- [ ] "Status" tab visible
- [ ] Can enter queries

### 7. Grafana (http://localhost:30300)
- [ ] Grafana loads
- [ ] Login page visible
- [ ] Login: admin / admin
- [ ] Dashboard appears
- [ ] Can create panels

### 8. Loki (http://localhost:30100)
- [ ] Page loads (shows 404 - expected)
- [ ] Used via Grafana, not directly

---

## 🚀 FIRST TIME SETUP (In Order)

### 1. Krayin CRM Application
```
URL: http://localhost:30080
Login: admin@example.com / admin123
Action: Explore the CRM interface
```

### 2. Jenkins Setup
```
URL: http://localhost:8082
Initial Password: 857a566964703a4cdf9597467c01d
Actions:
  1. Paste password
  2. Install plugins
  3. Create admin user
  4. Configure credentials (jfrog-creds, sonar-token)
  5. Create pipeline job
  6. Click "Build Now"
```

### 3. SonarQube Configuration
```
URL: http://localhost:9000
Login: admin / admin
Actions:
  1. Create project: "laravel-crm"
  2. Generate token
  3. Add to Jenkins credentials
```

### 4. Grafana Dashboard
```
URL: http://localhost:30300
Login: admin / admin
Actions:
  1. Add Prometheus datasource: http://prometheus:9090
  2. Add Loki datasource: http://loki.logging:3100
  3. Create dashboard
  4. Add panels for metrics
```

---

## 🔍 VERIFY DEPLOYMENT

Run these checks in your browser:

| Check | URL | Expected Result |
|-------|-----|-----------------|
| App Running | http://localhost:30080 | Login page loads |
| Admin Access | http://localhost:30080/admin/login | Login form visible |
| CI/CD Tool | http://localhost:8082 | Jenkins dashboard |
| Code Quality | http://localhost:9000 | SonarQube interface |
| Artifacts | http://localhost:8083 | Artifactory interface |
| Metrics | http://localhost:30090 | Prometheus graphs |
| Dashboards | http://localhost:30300 | Grafana panels |
| Logs Ready | http://localhost:30100 | API endpoint (404 OK) |

---

## 📝 NOTES

- All URLs use `localhost` (your machine)
- Different ports separate services
- Some URLs work immediately
- Some need initial setup (Jenkins, Grafana)
- Jenkins initial password is shown above - save it!
- All credentials are shown in login table above

---

## 🎯 MOST IMPORTANT FIRST STEPS

1. **Open and login to Krayin CRM:**
   ```
   http://localhost:30080
   admin@example.com / admin123
   ```

2. **Setup Jenkins:**
   ```
   http://localhost:8082
   Password: 857a566964703a4cdf9597467c01d
   ```

3. **Monitor with Grafana:**
   ```
   http://localhost:30300
   admin / admin
   ```

---

**Everything is running and ready to use! 🚀**
