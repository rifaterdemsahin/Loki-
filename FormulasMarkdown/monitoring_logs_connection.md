@rifaterdemsahin ➜ /workspaces/loki (main) $ kubectl get pods -n monitoring
NAME                       READY   STATUS    RESTARTS      AGE
grafana-59fb4f95f7-rkzwp   1/1     Running   0             31m
loki-0                     1/1     Running   2 (58m ago)   95m
loki-promtail-x7hvz        1/1     Running   1 (59m ago)   95m
@rifaterdemsahin ➜ /workspaces/loki (main) $ 
@rifaterdemsahin ➜ /workspaces/loki (main) $ kubectl logs -l app=loki --namespace monitoring
level=info ts=2024-10-14T19:23:05.021581242Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:23:05.021592785Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:23:05.02167573Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:24:04.891169748Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:24:04.891277701Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:24:04.891305955Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:24:05.021446078Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:24:05.021489975Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:24:05.021499964Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:24:05.021510059Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
@rifaterdemsahin ➜ /workspaces/loki (main) $ 