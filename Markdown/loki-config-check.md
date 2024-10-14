To check if `auth_enabled: false` is set in a running Loki instance on Minikube, follow these steps:

### 1. Access the Loki Pod:
First, identify the Loki pod running inside your Minikube cluster.

- List all the pods in your namespace (replace `<namespace>` with the correct namespace if needed, or omit if using the default):

   ```bash
   kubectl get pods -n <namespace>
   ```

- Find the Loki pod in the list, and then access it using:

   ```bash
   kubectl exec -it <pod_name> -n <namespace> -- /bin/sh
   ```

   or if Bash is available:

   ```bash
   kubectl exec -it <pod_name> -n <namespace> -- /bin/bash
   ```

### 2. Locate the Configuration File:
Once inside the Loki pod, you need to locate the `config.yaml` file, which stores the Loki configuration. Typically, it might be located in one of the following paths:

- `/etc/loki/`
- `/usr/local/etc/loki/`
- Check any custom paths used for your deployment

To locate the configuration file, use the `find` command:

```bash
find / -name config.yaml
```

### 3. Check the `auth_enabled` Setting:
Once you've located the configuration file, inspect it by using a command like `cat`, `vi`, or `nano`:

```bash
cat /path/to/config.yaml
```

Look for the following line in the file:

```yaml
auth_enabled: false
```

If this setting is missing or set to `true`, you may need to update it and restart the Loki pod for the changes to take effect.

### 4. Exit the Pod:
After checking or modifying the configuration, you can exit the Loki pod by typing:

```bash
exit
```

### 5. Restart the Loki Pod (if configuration is modified):
If you modified the configuration file, restart the Loki pod to apply the changes:

```bash
kubectl delete pod <pod_name> -n <namespace>
```

Kubernetes will automatically recreate the pod with the updated configuration.

Let me know if you need further assistance!