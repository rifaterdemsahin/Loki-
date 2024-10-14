Journey 1 > With Docker Environment
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
------------------------------------------------------------------------------------------

Journey 2 > With MinikubeEnvironment
### 1️⃣ Setup GitHub Codespaces

- Navigate to your GitHub repository.
- Click on **Codespaces** from the top menu.
- Select **New Codespace** to launch a new development environment.

### 2️⃣ Install Minikube

In your GitHub Codespaces terminal, follow these steps to install Minikube:

```bash
# Install Minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Start Minikube
minikube start
```

### 3️⃣ Install Loki and Promtail

Deploy Loki and Promtail using Helm charts:

```bash
# Add the Grafana Helm repository
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update

# Install Loki
helm install loki grafana/loki-stack --set promtail.enabled=true
```

### 4️⃣ Configure Loki

Loki and Promtail are pre-configured when installed via Helm. However, you can customize the configuration by editing the Helm values:

```bash
# Edit the Loki configuration
helm upgrade loki grafana/loki-stack --set-file loki.configs.loki.yaml=loki-config.yaml
```

### 5️⃣ Verify the Setup

Ensure that Loki and Promtail are running correctly by checking the services in Minikube:

```bash
# Get the list of services
kubectl get services

# Forward the Loki service port to localhost
kubectl port-forward service/loki 3100:3100
```

- **URL:** `http://localhost:3100/metrics`

You should see metrics reflecting logs being ingested.

### 6️⃣ Connect Grafana for Visualization (Optional)

To visualize logs more effectively, set up **Grafana** and link it to Loki as a data source:

```bash
# Install Grafana using Helm
helm install grafana grafana/grafana

# Forward the Grafana service port to localhost
kubectl port-forward service/grafana 3000:3000
```

- **Access Grafana at:** `http://localhost:3000`
- **Add Loki as a data source:** Use the URL `http://localhost:3100` for the Loki instance.
