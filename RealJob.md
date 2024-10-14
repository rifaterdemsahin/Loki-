# README: Implementing Loki in GitHub Codespaces for Log Aggregation

## 💡 What I Want to Achieve

The goal is to implement Loki as a log aggregation system within **GitHub Codespaces** to efficiently monitor containerized applications. Loki is ideal for its simplicity, lightweight nature, and ability to retrieve logs without heavy indexing. The aim is to create a **Proof of Concept (PoC)** for Loki in GitHub Codespaces, providing a quick setup that can be used in future development environments.

---

## 🛠️ Steps to Implement Loki in GitHub Codespaces

### 1️⃣ Setup GitHub Codespaces

- Navigate to your GitHub repository.
- Click on **Codespaces** from the top menu.
- Select **New Codespace** to launch a new development environment.

### 2️⃣ Install Loki and Promtail

In your GitHub Codespaces terminal, follow these steps:

```bash
# Clone the Loki repository to set up your log system
git clone https://github.com/grafana/loki.git
cd loki/

# Install Loki using Docker
docker run -d --name loki -p 3100:3100 grafana/loki:2.7.0
```

### 3️⃣ Configure Loki

Configure Loki to meet your log aggregation needs by creating a `loki-config.yaml` file. Customize settings such as log retention, scraping, and storage:

```yaml
auth_enabled: false
server:
  http_listen_port: 3100
ingester:
  lifecycler:
    ring:
      kvstore:
        store: inmemory
  chunk_idle_period: 5m
  chunk_retain_period: 30s
  max_transfer_retries: 0
schema_config:
  configs:
    - from: 2021-01-01
      store: boltdb
      object_store: filesystem
      schema: v11
      index:
        prefix: index_
        period: 168h
storage_config:
  boltdb:
    directory: /loki/index
  filesystem:
    directory: /loki/chunks
limits_config:
  enforce_metric_name: false
  reject_old_samples: true
  reject_old_samples_max_age: 168h
```

### 4️⃣ Install Promtail

Promtail is an agent that ships logs from your Codespace containers to Loki. Install it using Docker:

```bash
docker run -d --name promtail --link loki -v /var/log:/var/log -p 9080:9080 grafana/promtail:2.7.0
```

### 5️⃣ Verify the Setup

Ensure that Loki and Promtail are running correctly by visiting the Loki metrics page:

- **URL:** `http://localhost:3100/metrics`

You should see metrics reflecting logs being ingested.

### 6️⃣ Connect Grafana for Visualization (Optional)

To visualize logs more effectively, set up **Grafana** and link it to Loki as a data source:

```bash
docker run -d --name=grafana -p 3000:3000 grafana/grafana
```

- **Access Grafana at:** `http://localhost:3000`
- **Add Loki as a data source:** Use the URL `http://localhost:3100` for the Loki instance.

---

## 🎯 Result

By completing this setup, Loki and Promtail will be running in your GitHub Codespace, allowing you to efficiently track logs from your containerized applications.

---

## 🚀 Next Steps

- Optimize the **log scraping configurations**.
- Explore **alerting mechanisms** for critical logs.
- Integrate Loki into your **CI/CD pipeline** for automated monitoring during development.

---

## 🔗 Connect with Me

- 💼 LinkedIn: [https://www.linkedin.com/in/rifaterdemsahin/](https://www.linkedin.com/in/rifaterdemsahin/)
- 🐦 Twitter: [https://x.com/rifaterdemsahin](https://x.com/rifaterdemsahin)
- 🎥 YouTube: [https://www.youtube.com/@RifatErdemSahin](https://www.youtube.com/@RifatErdemSahin)
- 💻 GitHub: [https://github.com/rifaterdemsahin](https://github.com/rifaterdemsahin)

---

## 📝 Screenshot of the PoC in Action

Take screenshots of key moments during setup for future reference and blog posts!

--- 

