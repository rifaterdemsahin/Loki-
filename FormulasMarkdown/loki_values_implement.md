To implement the provided Loki configuration into your Minikube setup, you'll need to modify Loki's configuration file. Since you are using Helm to deploy Loki, you can follow these steps:

### Steps to Implement Custom Loki Configuration with Helm in Minikube:

1. **Download the Default Loki Values File**:
   You need to customize the default Helm values to add your specific configuration. Start by downloading the default Loki `values.yaml` file:
   ```bash
   helm show values grafana/loki-stack > loki-values.yaml
   ```

2. **Modify the Configuration**:
   Open the `loki-values.yaml` file and add your custom configuration under the appropriate sections.

   For the given config, you'll likely modify the `loki.config` section of the values file. For example:

   ```yaml
   loki:
     config:
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

   Ensure your custom configuration is in the correct format under the `config` section of Loki's Helm chart.

3. **Apply the Modified Configuration**:
   Once you have modified the `loki-values.yaml` file, you can apply it by running the Helm upgrade command:

   ```bash
    cd /workspaces/loki/Code/
   helm upgrade loki grafana/loki-stack --namespace monitoring -f loki-config.yaml
   ```

   This will apply the custom configuration to your existing Loki deployment.

4. **Verify the Deployment**:
   After applying the configuration, you can check if the Loki pods are running properly and pick up the new configuration by using:

   ```bash
   kubectl get pods -n monitoring
   ```

   Also, check the logs for any errors or configuration loading confirmation:

   ```bash
   kubectl logs -l app=loki --namespace monitoring
   ```

By following these steps, Loki will run with your custom configuration, including settings like `auth_enabled: false`, custom storage, and schema configurations.

Let me know if you need any further assistance!