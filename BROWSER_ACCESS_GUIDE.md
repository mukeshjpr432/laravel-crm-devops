# 🌐 BROWSER ACCESS GUIDE - COMPLETE INSTRUCTIONS

## Open These URLs in Your Browser

---

## 1️⃣ KRAYIN CRM APPLICATION (Main App)

### URL: `http://localhost:30080`

**What you'll see:**
- Krayin CRM home page
- Redirects to admin login

**How to access:**
1. Open your browser
2. Type: `http://localhost:30080`
3. Press Enter

**Login:**
```
Email: admin@example.com
Password: admin123
```

**What you can do:**
- View dashboard
- Manage customers
- Manage leads
- View reports
- Access all CRM features

---

## 2️⃣ KRAYIN CRM ADMIN LOGIN PAGE

### URL: `http://localhost:30080/admin/login`

**What you'll see:**
- Login page with email/password form
- Sign In button
- Forget Password link

**How to access:**
1. Open your browser
2. Type: `http://localhost:30080/admin/login`
3. Press Enter

**Credentials:**
```
Email: admin@example.com
Password: admin123
```

**Login Steps:**
1. Enter email: `admin@example.com`
2. Enter password: `admin123`
3. Click "Sign In"
4. You'll be redirected to admin dashboard

---

## 3️⃣ JENKINS - CI/CD PIPELINE

### URL: `http://localhost:8082`

**What you'll see:**
- Jenkins dashboard
- Setup wizard (first time)
- Job creation interface

**How to access:**
1. Open browser
2. Type: `http://localhost:8082`
3. Press Enter

**Initial Setup (First Time):**
1. Jenkins will show: "Unlock Jenkins"
2. Paste this password:
   ```
   857a566964964703a4cdf9597467c01d
   ```
3. Click "Continue"
4. Choose "Install suggested plugins"
5. Create admin user

**After Setup:**
- You can create pipeline jobs
- Configure credentials
- Trigger builds
- View build history
- Monitor pipeline executions

**Creating Your First Pipeline:**
1. Click "New Item"
2. Enter name: `krayin-crm-pipeline`
3. Select "Pipeline"
4. Click "OK"
5. Go to "Pipeline" section
6. Select "Pipeline script from SCM"
7. Choose "Git"
8. Enter repo: `https://github.com/mukeshjpr432/laravel-crm-devops.git`
9. Branch: `main`
10. Script path: `Jenkinsfile`
11. Save
12. Click "Build Now"

---

## 4️⃣ SONARQUBE - CODE QUALITY

### URL: `http://localhost:9000`

**What you'll see:**
- SonarQube dashboard
- Code quality metrics
- Project analysis results
- Vulnerabilities and bugs

**How to access:**
1. Open browser
2. Type: `http://localhost:9000`
3. Press Enter

**Default Credentials:**
```
Username: admin
Password: admin
```

**What you can do:**
- View code quality analysis
- Check PHP code issues
- Monitor security vulnerabilities
- Create projects
- Configure quality gates
- View historical trends

**First Time Setup:**
1. Login with admin/admin
2. Create new project
3. Project key: `laravel-crm`
4. Generate token
5. Use token in Jenkins

---

## 5️⃣ JFROG ARTIFACTORY - DOCKER REGISTRY

### URL: `http://localhost:8083`

**What you'll see:**
- Artifactory dashboard
- Docker repositories
- Artifact management
- Build info

**How to access:**
1. Open browser
2. Type: `http://localhost:8083`
3. Press Enter

**Credentials:**
```
Username: mukeshjpr432
Password: DoHare@1991
```

**What you can do:**
- View Docker images
- Browse repositories
- View image layers
- Check image metadata
- Manage artifact versions
- View upload/download stats

**First Time:**
1. Login with credentials above
2. Go to "Repositories"
3. Find "docker-local"
4. You'll see pushed images after Jenkins build

---

## 6️⃣ PROMETHEUS - METRICS COLLECTION

### URL: `http://localhost:30090`

**What you'll see:**
- Prometheus dashboard
- Metrics browser
- Graph visualization
- Target status

**How to access:**
1. Open browser
2. Type: `http://localhost:30090`
3. Press Enter

**No Login Required**

**What you can do:**
- Query metrics (Prometheus Query Language)
- Visualize metric graphs
- Check target health
- View scrape configs
- Create custom queries

**Example Queries to Try:**
```
up                           # Check if targets are up
container_memory_usage_bytes # Memory usage
rate(http_requests_total[5m]) # Request rate
node_cpu_seconds_total       # CPU metrics
```

**How to Query:**
1. Go to "Graph" tab
2. Enter a query in the "Expression" box
3. Click "Execute"
4. See results in graph

---

## 7️⃣ GRAFANA - DASHBOARDS & VISUALIZATION

### URL: `http://localhost:30300`

**What you'll see:**
- Grafana dashboard
- Pre-configured panels
- Login form
- Visualization gallery

**How to access:**
1. Open browser
2. Type: `http://localhost:30300`
3. Press Enter

**Default Credentials:**
```
Username: admin
Password: admin
```

**First Login:**
1. Enter admin/admin
2. It will prompt to change password (optional)
3. You'll see home dashboard

**What you can do:**
- View real-time metrics
- Create custom dashboards
- Add panels with graphs
- Connect Prometheus datasource
- Connect Loki datasource
- View application metrics
- View system health
- Create alerts

**Create Your First Dashboard:**
1. Click "+" (Create)
2. Select "Dashboard"
3. Click "Add panel"
4. Select data source: "Prometheus"
5. Enter query: `up`
6. Customize visualization
7. Save dashboard

**Add Loki for Logs:**
1. Go to "Configuration" → "Datasources"
2. Click "Add datasource"
3. Select "Loki"
4. URL: `http://loki.logging:3100`
5. Save
6. Create log panel with Loki queries

---

## 8️⃣ LOKI - LOG AGGREGATION

### URL: `http://localhost:30100`

**What you'll see:**
- Loki API endpoint (returns 404 for root)
- Log aggregation service running
- API ready for queries

**How to access:**
1. Open browser
2. Type: `http://localhost:30100`
3. Press Enter

**This is an API endpoint:**
- Direct browser access shows 404 (expected)
- Used by Grafana to query logs
- Access logs through Grafana interface instead

**Query Logs via Grafana:**
1. Open Grafana: `http://localhost:30300`
2. Go to "Explore"
3. Select data source: "Loki"
4. Write query: `{app="krayin-crm"}`
5. Click "Run query"
6. View logs

---

## 📋 QUICK BROWSER BOOKMARKS

Save these URLs as bookmarks in your browser:

```
1. Krayin CRM          → http://localhost:30080
2. Admin Panel         → http://localhost:30080/admin/login
3. Jenkins             → http://localhost:8082
4. SonarQube           → http://localhost:9000
5. Artifactory         → http://localhost:8083
6. Prometheus          → http://localhost:30090
7. Grafana             → http://localhost:30300
8. Loki API            → http://localhost:30100
```

---

## 🔐 CREDENTIALS REFERENCE

Keep this handy:

```
KRAYIN CRM APPLICATION
├─ URL: http://localhost:30080
├─ Admin: http://localhost:30080/admin/login
├─ Email: admin@example.com
└─ Password: admin123

JENKINS
├─ URL: http://localhost:8082
├─ Initial Password: 857a566964964703a4cdf9597467c01d
└─ (Create admin after first login)

SONARQUBE
├─ URL: http://localhost:9000
├─ Username: admin
└─ Password: admin

JFROG ARTIFACTORY
├─ URL: http://localhost:8083
├─ Username: mukeshjpr432
└─ Password: DoHare@1991

GRAFANA
├─ URL: http://localhost:30300
├─ Username: admin
└─ Password: admin

PROMETHEUS
├─ URL: http://localhost:30090
└─ No Login Required

LOKI
├─ URL: http://localhost:30100
└─ API Endpoint (use via Grafana)
```

---

## ✅ VERIFICATION CHECKLIST

After opening each URL in browser, you should see:

- [ ] **Krayin CRM (30080)** → Redirects to admin login / Shows CRM interface
- [ ] **Admin Login (30080/admin/login)** → Shows login form with email/password fields
- [ ] **Jenkins (8082)** → Shows Jenkins dashboard or setup wizard
- [ ] **SonarQube (9000)** → Shows SonarQube interface or login
- [ ] **Artifactory (8083)** → Shows Artifactory dashboard
- [ ] **Prometheus (30090)** → Shows Prometheus query interface
- [ ] **Grafana (30300)** → Shows Grafana dashboard or login
- [ ] **Loki (30100)** → Shows API response

---

## 🚀 NEXT STEPS IN BROWSER

### Step 1: Login to Krayin CRM
1. Open: `http://localhost:30080`
2. Login with `admin@example.com` / `admin123`
3. Explore the dashboard

### Step 2: Setup Jenkins
1. Open: `http://localhost:8082`
2. Paste initial password: `857a566964964703a4cdf9597467c01d`
3. Install plugins
4. Create admin user
5. Create pipeline job

### Step 3: Add Jenkins Credentials
1. Go to Jenkins dashboard
2. Click "Manage Jenkins"
3. Select "Credentials"
4. Add new credentials:
   - **jfrog-creds**: mukeshjpr432 / DoHare@1991
   - **sonar-token**: any token value

### Step 4: Create Pipeline Job
1. Click "New Item"
2. Name: `krayin-crm-pipeline`
3. Select "Pipeline"
4. Pipeline script from SCM
5. Git repo: `https://github.com/mukeshjpr432/laravel-crm-devops.git`
6. Branch: `main`
7. Script path: `Jenkinsfile`
8. Save
9. Click "Build Now"

### Step 5: Monitor with Prometheus & Grafana
1. Open Prometheus: `http://localhost:30090`
2. Query metrics: `up` or `container_memory_usage_bytes`
3. Open Grafana: `http://localhost:30300`
4. Login: admin / admin
5. Create dashboard with Prometheus datasource
6. Add Loki for logs

### Step 6: Check Code Quality
1. Open SonarQube: `http://localhost:9000`
2. Login: admin / admin
3. Create project: `laravel-crm`
4. After Jenkins build, results will appear

### Step 7: View Docker Images
1. Open Artifactory: `http://localhost:8083`
2. Login: mukeshjpr432 / DoHare@1991
3. Navigate to "docker-local" repository
4. You'll see images after Jenkins push

---

## 📊 MONITORING DASHBOARD WORKFLOW

1. **Prometheus (30090)**
   - Check metrics are being collected
   - Run test queries

2. **Grafana (30300)**
   - Login: admin / admin
   - Add Prometheus datasource
   - Create dashboard
   - Add Loki datasource
   - Create log panels
   - Set up alerts

3. **Loki (30100)**
   - Access via Grafana Explore
   - Query: `{app="krayin-crm"}`
   - View application logs in real-time

---

## 🎯 TROUBLESHOOTING - URL NOT OPENING

If a URL doesn't open:

### Check 1: Is the service running?
```bash
docker ps                    # Check Docker containers
kubectl get pods -A          # Check Kubernetes pods
```

### Check 2: Check port is listening
```bash
netstat -ano | findstr :PORT_NUMBER  # Windows
lsof -i :PORT_NUMBER                 # Mac/Linux
```

### Check 3: Restart service
```bash
docker restart CONTAINER_NAME        # Docker containers
kubectl rollout restart deployment/NAME -n NAMESPACE  # Kubernetes
```

### Check 4: View logs
```bash
docker logs CONTAINER_NAME           # Docker
kubectl logs POD_NAME -n NAMESPACE   # Kubernetes
```

---

## 💡 TIPS FOR BROWSER ACCESS

1. **Bookmark all URLs** for quick access
2. **Use Chrome DevTools** (F12) to debug issues
3. **Check browser console** for error messages
4. **Clear browser cache** if pages don't load: Ctrl+Shift+Delete
5. **Use Incognito mode** if having session issues
6. **Check firewall** if ports are blocked

---

## ✨ YOU'RE ALL SET!

All services are running and accessible through your browser. 

**Start here:** Open `http://localhost:30080` and login with:
- Email: `admin@example.com`
- Password: `admin123`

Then explore Jenkins, SonarQube, Grafana, and other tools!

---

**Happy Monitoring! 🚀**
