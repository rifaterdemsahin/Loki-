Promtail is an agent that ships logs from your Codespace containers to Loki. Install it using Docker:

```bash
docker run -d --name promtail --link loki -v /var/log:/var/log -p 9080:9080 grafana/promtail:2.7.0
```

Minikube

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
    name: promtail-config
    namespace: default
data:
    promtail.yaml: |
        server:
            http_listen_port: 9080
        clients:
            - url: http://loki:3100/loki/api/v1/push
        positions:
            filename: /var/log/positions.yaml
        scrape_configs:
            - job_name: system
                static_configs:
                    - targets:
                            - localhost
                        labels:
                            job: varlogs
                            __path__: /var/log/*log
---
apiVersion: apps/v1
kind: DaemonSet
metadata:
    name: promtail
    namespace: default
    labels:
        app: promtail
spec:
    selector:
        matchLabels:
            name: promtail
    template:
        metadata:
            labels:
                name: promtail
        spec:
            containers:
                - name: promtail
                    image: grafana/promtail:2.7.0
                    args:
                        - -config.file=/etc/promtail/promtail.yaml
                    volumeMounts:
                        - name: config
                            mountPath: /etc/promtail
                        - name: varlog
                            mountPath: /var/log
            volumes:
                - name: config
                    configMap:
                        name: promtail-config
                - name: varlog
                    hostPath:
                        path: /var/log
                        type: Directory
```


```bash
kubectl apply -f promtail.yaml
```

