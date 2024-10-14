To check the running logs of Loki in your Kubernetes cluster, you can use `kubectl logs` to access the logs from the Loki pods.

Here are the steps to follow:

### 1. **Identify the Loki Pod**:
   First, you'll need to get the name of the running Loki pod. You can do this by running:

   ```bash
   kubectl get pods -n monitoring
   ```

   This will list all the pods in the `monitoring` namespace, and you'll see the name of the Loki pod(s). It should look something like `loki-xxxxx`.

### 2. **Check the Logs**:
   Once you have the name of the Loki pod, use `kubectl logs` to view the logs:

   ```bash
   kubectl logs <loki-pod-name> -n monitoring
   ```

   For example, if the Loki pod name is `loki-abcdef1234-xyz`, you would run:

   ```bash
   kubectl logs loki-abcdef1234-xyz -n monitoring
   ```

   This will show you the logs from the Loki pod.

### 3. **Tail the Logs (Optional)**:
   If you want to stream the logs and monitor them in real time, you can use the `-f` flag (similar to `tail -f`):

   ```bash
   kubectl logs -f <loki-pod-name> -n monitoring
   ```

This will keep showing you logs as they come in, which is helpful for monitoring Loki in real-time.

Let me know if you need more guidance!


rifaterdemsahin ➜ /workspaces/loki (main) $ kubectl logs -f loki-0 -n monitoring
level=info ts=2024-10-14T18:26:04.871940336Z caller=main.go:103 msg="Starting Loki" version="(version=2.6.1, branch=HEAD, revision=6bd05c9a4)"
level=info ts=2024-10-14T18:26:04.872672179Z caller=server.go:288 http=[::]:3100 grpc=[::]:9095 msg="server listening on addresses"
level=info ts=2024-10-14T18:26:04.873193903Z caller=modules.go:736 msg="RulerStorage is not configured in single binary mode and will not be started."
level=warn ts=2024-10-14T18:26:04.881647633Z caller=experimental.go:20 msg="experimental feature in use" feature="In-memory (FIFO) cache - chunksfifocache"
level=info ts=2024-10-14T18:26:04.88252765Z caller=table_manager.go:252 msg="query readiness setup completed" duration=1.918µs distinct_users_len=0
level=info ts=2024-10-14T18:26:04.882594022Z caller=shipper.go:124 msg="starting index shipper in RW mode"
level=info ts=2024-10-14T18:26:04.882712936Z caller=table_manager.go:226 msg="loading table index_20010"
level=info ts=2024-10-14T18:26:04.882954048Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:26:04.883009102Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:26:04.883048783Z caller=shipper_index_client.go:79 msg="starting boltdb shipper in RW mode"
level=info ts=2024-10-14T18:26:04.883350957Z caller=modules.go:761 msg="RulerStorage is nil.  Not starting the ruler."
level=info ts=2024-10-14T18:26:04.884211072Z caller=worker.go:112 msg="Starting querier worker using query-scheduler and scheduler ring for addresses"
level=info ts=2024-10-14T18:26:04.889830674Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:26:04.889889105Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:26:04.890862264Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:26:04.890941822Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:26:04.890952508Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:26:04.895098015Z caller=module_service.go:82 msg=initialising module=server
level=info ts=2024-10-14T18:26:04.895458087Z caller=module_service.go:82 msg=initialising module=memberlist-kv
level=info ts=2024-10-14T18:26:04.89549484Z caller=module_service.go:82 msg=initialising module=query-frontend-tripperware
level=info ts=2024-10-14T18:26:04.895516951Z caller=module_service.go:82 msg=initialising module=store
level=info ts=2024-10-14T18:26:04.895530272Z caller=module_service.go:82 msg=initialising module=ring
level=info ts=2024-10-14T18:26:04.895597723Z caller=ring.go:263 msg="ring doesn't exist in KV store yet"
level=info ts=2024-10-14T18:26:04.895699481Z caller=module_service.go:82 msg=initialising module=usage-report
level=info ts=2024-10-14T18:26:04.89599911Z caller=module_service.go:82 msg=initialising module=ingester-querier
level=info ts=2024-10-14T18:26:04.896032079Z caller=module_service.go:82 msg=initialising module=ingester
level=info ts=2024-10-14T18:26:04.896049109Z caller=ingester.go:401 msg="recovering from checkpoint"
level=info ts=2024-10-14T18:26:04.89746843Z caller=module_service.go:82 msg=initialising module=distributor
level=info ts=2024-10-14T18:26:04.897889248Z caller=module_service.go:82 msg=initialising module=compactor
level=info ts=2024-10-14T18:26:04.898199994Z caller=ring.go:263 msg="ring doesn't exist in KV store yet"
level=info ts=2024-10-14T18:26:04.898325577Z caller=module_service.go:82 msg=initialising module=query-scheduler
level=info ts=2024-10-14T18:26:04.898534752Z caller=ring.go:263 msg="ring doesn't exist in KV store yet"
level=info ts=2024-10-14T18:26:04.898604983Z caller=ring.go:263 msg="ring doesn't exist in KV store yet"
level=info ts=2024-10-14T18:26:04.898696206Z caller=basic_lifecycler.go:261 msg="instance not found in the ring" instance=loki-0 ring=compactor
level=info ts=2024-10-14T18:26:04.898716242Z caller=basic_lifecycler_delegates.go:63 msg="not loading tokens from file, tokens file path is empty"
level=info ts=2024-10-14T18:26:04.89906253Z caller=memberlist_client.go:534 msg="joined memberlist cluster" reached_nodes=1
level=info ts=2024-10-14T18:26:04.899435823Z caller=basic_lifecycler.go:261 msg="instance not found in the ring" instance=loki-0 ring=scheduler
level=info ts=2024-10-14T18:26:04.899466122Z caller=basic_lifecycler_delegates.go:63 msg="not loading tokens from file, tokens file path is empty"
level=info ts=2024-10-14T18:26:04.89966343Z caller=compactor.go:307 msg="waiting until compactor is JOINING in the ring"
level=info ts=2024-10-14T18:26:04.899683311Z caller=compactor.go:311 msg="compactor is JOINING in the ring"
level=info ts=2024-10-14T18:26:04.899758656Z caller=scheduler.go:617 msg="waiting until scheduler is JOINING in the ring"
level=info ts=2024-10-14T18:26:04.899771807Z caller=scheduler.go:621 msg="scheduler is JOINING in the ring"
level=info ts=2024-10-14T18:26:04.899843182Z caller=lifecycler.go:547 msg="not loading tokens from file, tokens file path is empty"
level=info ts=2024-10-14T18:26:04.899901495Z caller=lifecycler.go:576 msg="instance not found in ring, adding with no tokens" ring=distributor
level=info ts=2024-10-14T18:26:04.900319394Z caller=lifecycler.go:416 msg="auto-joining cluster after timeout" ring=distributor
level=info ts=2024-10-14T18:26:04.900637703Z caller=ingester.go:417 msg="recovered WAL checkpoint recovery finished" elapsed=4.595829ms errors=false
level=info ts=2024-10-14T18:26:04.900657677Z caller=ingester.go:423 msg="recovering from WAL"
level=info ts=2024-10-14T18:26:04.901787493Z caller=ingester.go:439 msg="WAL segment recovery finished" elapsed=5.745694ms errors=false
level=info ts=2024-10-14T18:26:04.901878463Z caller=ingester.go:387 msg="closing recoverer"
level=info ts=2024-10-14T18:26:04.901950931Z caller=ingester.go:395 msg="WAL recovery finished" time=5.908684ms
level=info ts=2024-10-14T18:26:04.902065882Z caller=wal.go:156 msg=started component=wal
level=info ts=2024-10-14T18:26:04.902094439Z caller=lifecycler.go:547 msg="not loading tokens from file, tokens file path is empty"
level=info ts=2024-10-14T18:26:04.90218923Z caller=lifecycler.go:576 msg="instance not found in ring, adding with no tokens" ring=ingester
level=info ts=2024-10-14T18:26:04.902268757Z caller=lifecycler.go:416 msg="auto-joining cluster after timeout" ring=ingester
level=info ts=2024-10-14T18:26:05.021119233Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:26:05.021163756Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:26:05.900234805Z caller=scheduler.go:631 msg="waiting until scheduler is ACTIVE in the ring"
level=info ts=2024-10-14T18:26:05.900315667Z caller=compactor.go:321 msg="waiting until compactor is ACTIVE in the ring"
level=info ts=2024-10-14T18:26:06.004851984Z caller=scheduler.go:635 msg="scheduler is ACTIVE in the ring"
level=info ts=2024-10-14T18:26:06.004937649Z caller=module_service.go:82 msg=initialising module=querier
level=info ts=2024-10-14T18:26:06.005460325Z caller=module_service.go:82 msg=initialising module=query-frontend
level=info ts=2024-10-14T18:26:06.084860177Z caller=compactor.go:325 msg="compactor is ACTIVE in the ring"
level=info ts=2024-10-14T18:26:06.084917788Z caller=loki.go:374 msg="Loki started"
level=info ts=2024-10-14T18:26:09.005384611Z caller=scheduler.go:682 msg="this scheduler is in the ReplicationSet, will now accept requests."
level=info ts=2024-10-14T18:26:09.006464408Z caller=worker.go:209 msg="adding connection" addr=10.244.0.8:9095
level=info ts=2024-10-14T18:26:11.085999084Z caller=compactor.go:386 msg="this instance has been chosen to run the compactor, starting compactor"
level=info ts=2024-10-14T18:26:11.086069311Z caller=compactor.go:413 msg="waiting 10m0s for ring to stay stable and previous compactions to finish before starting compactor"
level=info ts=2024-10-14T18:26:16.005585603Z caller=frontend_scheduler_worker.go:101 msg="adding connection to scheduler" addr=10.244.0.8:9095
level=info ts=2024-10-14T18:27:04.891692434Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:27:04.891780343Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:27:04.89179849Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:27:05.021618474Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:27:05.021672153Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:27:05.021683377Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:27:05.02169422Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:28:04.891678169Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:28:04.891757455Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:28:04.891775327Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:28:05.021811685Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:28:05.021853603Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:28:05.021863668Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:28:05.021873035Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:29:04.891715976Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:29:04.892060072Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:29:04.892198038Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:29:05.021460434Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:29:05.021502006Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:29:05.021512866Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:29:05.021521567Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:30:04.891988303Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:30:04.892114859Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:30:04.89214928Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:30:05.022226591Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:30:05.022269727Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:30:05.022278293Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:30:05.022286232Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:31:04.891030535Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:31:04.891035795Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T18:31:04.891211794Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:31:04.891375132Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:31:04.891268167Z caller=table_manager.go:252 msg="query readiness setup completed" duration=1.846µs distinct_users_len=0
level=info ts=2024-10-14T18:31:04.902904287Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T18:31:04.903082607Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000009
level=info ts=2024-10-14T18:31:05.021515375Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:31:05.021589829Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:31:05.077275395Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:31:05.077316781Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:32:04.892023615Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:32:04.892136034Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:32:04.892169298Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:32:05.021233475Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:32:05.021298049Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:32:05.021310381Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:32:05.021392219Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:33:04.891180437Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:33:04.891276947Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:33:04.891327039Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:33:05.021509018Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:33:05.021631364Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:33:05.021660067Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:33:05.021684607Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:33:19.929064008Z caller=checkpoint.go:502 msg="atomic checkpoint finished" old=/data/loki/wal/checkpoint.000009.tmp new=/data/loki/wal/checkpoint.000009
level=info ts=2024-10-14T18:33:19.929485511Z caller=checkpoint.go:573 msg="checkpoint done" time=2m15.026166728s
level=info ts=2024-10-14T18:34:04.891482454Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:34:04.891625265Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:34:04.891675067Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:34:05.021726124Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:34:05.021784837Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:34:05.021795895Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:34:05.021959246Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:35:04.891943661Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:35:04.892104493Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:35:04.892128584Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:35:05.021973302Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:35:05.022028147Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:35:05.022040653Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:35:05.022050417Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:36:04.892837361Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:36:04.892950734Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T18:36:04.893076934Z caller=table_manager.go:252 msg="query readiness setup completed" duration=1.939µs distinct_users_len=0
level=info ts=2024-10-14T18:36:04.893241002Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:36:04.893308087Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:36:04.903160154Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T18:36:04.903453053Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000010
level=info ts=2024-10-14T18:36:05.021677853Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:36:05.021729261Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:36:05.021741244Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:36:05.021755072Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:36:11.086693774Z caller=compactor.go:418 msg="compactor startup delay completed"
level=info ts=2024-10-14T18:36:11.086740372Z caller=compactor.go:469 msg="compactor started"
ts=2024-10-14T18:36:11.086810589Z caller=spanlogger.go:80 level=info msg="building index list cache"
ts=2024-10-14T18:36:11.087031653Z caller=spanlogger.go:80 level=info msg="index list cache built" duration=111.786µs
level=info ts=2024-10-14T18:36:11.087061882Z caller=compactor.go:552 msg="compacting table" table-name=index_20010
level=info ts=2024-10-14T18:36:11.087156895Z caller=table.go:138 table-name=index_20010 msg="listed files" count=5
level=info ts=2024-10-14T18:36:11.087176382Z caller=table.go:297 table-name=index_20010 msg="starting compaction of dbs"
level=info ts=2024-10-14T18:36:11.087207338Z caller=table.go:307 table-name=index_20010 msg="using compactor-1728929955.gz as seed file"
level=info ts=2024-10-14T18:36:11.087978426Z caller=util.go:116 table-name=index_20010 file-name=compactor-1728929955.gz msg="downloaded file" total_time=756.687µs
level=info ts=2024-10-14T18:36:11.089837249Z caller=util.go:116 table-name=index_20010 file-name=loki-0-1728928149685619380-1728928800.gz msg="downloaded file" total_time=1.72966ms
level=info ts=2024-10-14T18:36:11.089958628Z caller=util.go:116 table-name=index_20010 file-name=loki-0-1728928149685619380-1728930310.gz msg="downloaded file" total_time=1.215262ms
level=info ts=2024-10-14T18:36:11.090039662Z caller=util.go:116 table-name=index_20010 file-name=loki-0-1728928149685619380-1728929700.gz msg="downloaded file" total_time=1.938364ms
level=info ts=2024-10-14T18:36:11.090609298Z caller=util.go:116 table-name=index_20010 file-name=loki-0-1728928149685619380-1728930364.gz msg="downloaded file" total_time=1.316521ms
level=info ts=2024-10-14T18:36:11.100691616Z caller=util.go:136 msg="compressing the file" src=/data/loki/boltdb-shipper-compactor/index_20010/compactor-1728929955.gz dest=/data/loki/boltdb-shipper-compactor/index_20010/compactor-1728929955.gz.gz
level=info ts=2024-10-14T18:36:11.116521149Z caller=index_set.go:281 table-name=index_20010 msg="removing source db files from storage" count=5
level=info ts=2024-10-14T18:36:11.116819895Z caller=compactor.go:557 msg="finished compacting table" table-name=index_20010
level=info ts=2024-10-14T18:37:04.891817048Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:37:04.891909444Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:37:04.8919268Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:37:05.022097076Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:37:05.02219914Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:37:05.022216275Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:37:05.022227083Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:38:04.891533997Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:38:04.891675925Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:38:04.891740839Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:38:05.021855004Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:38:05.02189637Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:38:05.02190705Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:38:05.021916469Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:39:04.891236028Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:39:04.891319822Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:39:04.891336401Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:39:05.02150726Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:39:05.021553314Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:39:05.021603504Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:39:05.021621018Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:40:04.891131932Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:40:04.891278153Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:40:04.891318325Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:40:05.021341819Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:40:05.021389078Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:40:05.021401502Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:40:05.021411078Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:40:34.929919783Z caller=checkpoint.go:502 msg="atomic checkpoint finished" old=/data/loki/wal/checkpoint.000010.tmp new=/data/loki/wal/checkpoint.000010
level=info ts=2024-10-14T18:40:34.930191197Z caller=checkpoint.go:573 msg="checkpoint done" time=4m30.026443896s
level=info ts=2024-10-14T18:41:04.891448077Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T18:41:04.891558587Z caller=table_manager.go:252 msg="query readiness setup completed" duration=1.87µs distinct_users_len=0
level=info ts=2024-10-14T18:41:04.891440902Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:41:04.89165957Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:41:04.891678241Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:41:04.902316913Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T18:41:04.902496358Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000011
level=info ts=2024-10-14T18:41:05.021708547Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:41:05.021752554Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:41:05.021766443Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:41:05.021775515Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:42:04.89159715Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:42:04.89166585Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:42:04.891748222Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:42:05.021825789Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:42:05.021869883Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:42:05.021880978Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:42:05.021890623Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:43:04.891672936Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:43:04.891935183Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:43:04.892023449Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:43:05.02160621Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:43:05.021650828Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:43:05.021661849Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:43:05.021671579Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:44:04.891300038Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:44:04.89137759Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:44:04.891392249Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:44:05.021453446Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:44:05.021498794Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:44:05.021517564Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:44:05.021528274Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:45:04.891646709Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:45:04.891745042Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:45:04.891758909Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:45:05.021388397Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:45:05.021459096Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:45:05.021471894Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:45:05.021481081Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:45:34.920137717Z caller=checkpoint.go:502 msg="atomic checkpoint finished" old=/data/loki/wal/checkpoint.000011.tmp new=/data/loki/wal/checkpoint.000011
level=info ts=2024-10-14T18:45:34.920414145Z caller=checkpoint.go:573 msg="checkpoint done" time=4m30.017738454s
level=info ts=2024-10-14T18:46:04.891680718Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:46:04.891889263Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T18:46:04.891912045Z caller=table_manager.go:252 msg="query readiness setup completed" duration=1.924µs distinct_users_len=0
level=info ts=2024-10-14T18:46:04.891991667Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:46:04.892010234Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:46:04.909709271Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T18:46:04.910154315Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000012
level=info ts=2024-10-14T18:46:05.021423052Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:46:05.021467044Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:46:05.060500007Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:46:05.060536244Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
ts=2024-10-14T18:46:11.116916562Z caller=spanlogger.go:80 level=info msg="building index list cache"
ts=2024-10-14T18:46:11.117073282Z caller=spanlogger.go:80 level=info msg="index list cache built" duration=93.501µs
level=info ts=2024-10-14T18:46:11.117112451Z caller=compactor.go:552 msg="compacting table" table-name=index_20010
level=info ts=2024-10-14T18:46:11.117207149Z caller=table.go:138 table-name=index_20010 msg="listed files" count=2
level=info ts=2024-10-14T18:46:11.117222756Z caller=table.go:297 table-name=index_20010 msg="starting compaction of dbs"
level=info ts=2024-10-14T18:46:11.117253591Z caller=table.go:307 table-name=index_20010 msg="using compactor-1728930971.gz as seed file"
level=info ts=2024-10-14T18:46:11.119006275Z caller=util.go:116 table-name=index_20010 file-name=compactor-1728930971.gz msg="downloaded file" total_time=1.742019ms
level=info ts=2024-10-14T18:46:11.119441865Z caller=util.go:116 table-name=index_20010 file-name=loki-0-1728928149685619380-1728930600.gz msg="downloaded file" total_time=300.871µs
level=info ts=2024-10-14T18:46:11.144570449Z caller=util.go:136 msg="compressing the file" src=/data/loki/boltdb-shipper-compactor/index_20010/compactor-1728930971.gz dest=/data/loki/boltdb-shipper-compactor/index_20010/compactor-1728930971.gz.gz
level=info ts=2024-10-14T18:46:11.170015439Z caller=index_set.go:281 table-name=index_20010 msg="removing source db files from storage" count=2
level=info ts=2024-10-14T18:46:11.170275726Z caller=compactor.go:557 msg="finished compacting table" table-name=index_20010
level=info ts=2024-10-14T18:47:04.891783396Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:47:04.891890731Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:47:04.891905045Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:47:05.021854294Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:47:05.021900953Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:47:05.021912372Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:47:05.021938349Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:48:04.89167073Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:48:04.891747409Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:48:04.891763626Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:48:05.021929455Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:48:05.021972192Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:48:05.021983281Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:48:05.022050826Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:49:04.891533061Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:49:04.89162306Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:49:04.891665115Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:49:05.021835981Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:49:05.021884978Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:49:05.021896513Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:49:05.021976122Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:50:04.891689203Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:50:04.891810827Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:50:04.891840855Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:50:05.022121515Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:50:05.022166034Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:50:05.022176535Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:50:05.022188463Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:50:34.949220669Z caller=checkpoint.go:502 msg="atomic checkpoint finished" old=/data/loki/wal/checkpoint.000012.tmp new=/data/loki/wal/checkpoint.000012
level=info ts=2024-10-14T18:50:34.949459613Z caller=checkpoint.go:573 msg="checkpoint done" time=4m30.038948242s
level=info ts=2024-10-14T18:51:04.891905269Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:51:04.892107125Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:51:04.892127556Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:51:04.891911446Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T18:51:04.892240027Z caller=table_manager.go:252 msg="query readiness setup completed" duration=2.838µs distinct_users_len=0
level=info ts=2024-10-14T18:51:04.902787399Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T18:51:04.903001925Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000013
level=info ts=2024-10-14T18:51:05.022137825Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:51:05.022185018Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:51:05.022195897Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:51:05.022208481Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:52:04.891669698Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:52:04.891736392Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:52:04.891749164Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:52:05.02195239Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:52:05.022002252Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:52:05.022013508Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:52:05.022025022Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:53:04.891443649Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:53:04.891591955Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:53:04.89168406Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:53:05.021810461Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:53:05.021855294Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:53:05.021866552Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:53:05.021875205Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:54:04.89159159Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:54:04.891675658Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:54:04.891695221Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:54:05.021890816Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:54:05.021933407Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:54:05.021944341Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:54:05.021962171Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:55:04.891929962Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:55:04.892048626Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:55:04.892064466Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:55:05.021340167Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:55:05.021391304Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:55:05.02140298Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:55:05.021412621Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:55:34.941690939Z caller=checkpoint.go:502 msg="atomic checkpoint finished" old=/data/loki/wal/checkpoint.000013.tmp new=/data/loki/wal/checkpoint.000013
level=info ts=2024-10-14T18:55:34.946156182Z caller=checkpoint.go:573 msg="checkpoint done" time=4m30.042914884s
level=info ts=2024-10-14T18:56:04.891491595Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:56:04.89158351Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:56:04.8916172Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:56:04.892510064Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T18:56:04.89303383Z caller=table_manager.go:252 msg="query readiness setup completed" duration=452.123µs distinct_users_len=0
level=info ts=2024-10-14T18:56:04.902484708Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T18:56:04.902689721Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000014
level=info ts=2024-10-14T18:56:05.02219787Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:56:05.022291269Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:56:05.022323788Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:56:05.022671443Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
ts=2024-10-14T18:56:11.117275588Z caller=spanlogger.go:80 level=info msg="building index list cache"
ts=2024-10-14T18:56:11.117573145Z caller=spanlogger.go:80 level=info msg="index list cache built" duration=92.829µs
level=info ts=2024-10-14T18:56:11.117632428Z caller=compactor.go:552 msg="compacting table" table-name=index_20010
level=info ts=2024-10-14T18:56:11.117910774Z caller=table.go:138 table-name=index_20010 msg="listed files" count=1
level=info ts=2024-10-14T18:56:11.118075654Z caller=compactor.go:557 msg="finished compacting table" table-name=index_20010
level=info ts=2024-10-14T18:57:04.891919298Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:57:04.892024702Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:57:04.892070435Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:57:05.022141697Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:57:05.022181542Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:57:05.022190274Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:57:05.022212538Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:58:04.891694784Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:58:04.891809529Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:58:04.891853581Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:58:05.022200946Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:58:05.022238158Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:58:05.022248576Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:58:05.02227399Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:59:04.89195677Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T18:59:04.892079241Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T18:59:04.892110412Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T18:59:05.021441428Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T18:59:05.021552214Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T18:59:05.021568195Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T18:59:05.021577351Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T18:59:56.376128601Z caller=checkpoint.go:502 msg="atomic checkpoint finished" old=/data/loki/wal/checkpoint.000014.tmp new=/data/loki/wal/checkpoint.000014
level=info ts=2024-10-14T18:59:56.376427382Z caller=checkpoint.go:573 msg="checkpoint done" time=3m51.469931856s
level=info ts=2024-10-14T19:00:04.891831794Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:00:04.891943939Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:00:04.891979456Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:00:05.021975601Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:00:05.022019437Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:00:05.022031031Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:00:05.022060006Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:01:04.891522339Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T19:01:04.891571276Z caller=table_manager.go:252 msg="query readiness setup completed" duration=1.656µs distinct_users_len=0
level=info ts=2024-10-14T19:01:04.891516362Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:01:04.89175648Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:01:04.891839762Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:01:04.902439653Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T19:01:04.902684958Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000015
level=info ts=2024-10-14T19:01:05.021836355Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:01:05.021921666Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:01:05.056145305Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:01:05.056183396Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:02:04.891666236Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:02:04.891776059Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:02:04.891807115Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:02:05.021845255Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:02:05.021900419Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:02:05.02191193Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:02:05.022014542Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:03:04.891534843Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:03:04.891627437Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:03:04.891661587Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:03:05.021749457Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:03:05.021820092Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:03:05.021832405Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:03:05.021841608Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:04:04.892048981Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:04:04.892133092Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:04:04.892171574Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:04:05.021695036Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:04:05.021741728Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:04:05.021754373Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:04:05.021797043Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:05:04.89169709Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:05:04.891852412Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:05:04.891911741Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:05:05.021888645Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:05:05.021933288Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:05:05.021942134Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:05:05.021950137Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:05:34.960932408Z caller=checkpoint.go:502 msg="atomic checkpoint finished" old=/data/loki/wal/checkpoint.000015.tmp new=/data/loki/wal/checkpoint.000015
level=info ts=2024-10-14T19:05:34.961415326Z caller=checkpoint.go:573 msg="checkpoint done" time=4m30.058539939s
level=info ts=2024-10-14T19:06:04.891567322Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T19:06:04.89166227Z caller=table_manager.go:252 msg="query readiness setup completed" duration=1.799µs distinct_users_len=0
level=info ts=2024-10-14T19:06:04.891561974Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:06:04.891832341Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:06:04.891848329Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:06:04.902365047Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T19:06:04.902554131Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000016
level=info ts=2024-10-14T19:06:05.022242214Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:06:05.022380341Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:06:05.022413069Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:06:05.022463479Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
ts=2024-10-14T19:06:11.117796051Z caller=spanlogger.go:80 level=info msg="building index list cache"
ts=2024-10-14T19:06:11.118104329Z caller=spanlogger.go:80 level=info msg="index list cache built" duration=213.611µs
level=info ts=2024-10-14T19:06:11.118166066Z caller=compactor.go:552 msg="compacting table" table-name=index_20010
level=info ts=2024-10-14T19:06:11.11828671Z caller=table.go:138 table-name=index_20010 msg="listed files" count=2
level=info ts=2024-10-14T19:06:11.118317714Z caller=table.go:297 table-name=index_20010 msg="starting compaction of dbs"
level=info ts=2024-10-14T19:06:11.118359547Z caller=table.go:307 table-name=index_20010 msg="using compactor-1728931571.gz as seed file"
level=info ts=2024-10-14T19:06:11.123502191Z caller=util.go:116 table-name=index_20010 file-name=compactor-1728931571.gz msg="downloaded file" total_time=5.128925ms
level=info ts=2024-10-14T19:06:11.126980348Z caller=util.go:116 table-name=index_20010 file-name=loki-0-1728928149685619380-1728931500.gz msg="downloaded file" total_time=250.463µs
level=info ts=2024-10-14T19:06:11.137788133Z caller=util.go:136 msg="compressing the file" src=/data/loki/boltdb-shipper-compactor/index_20010/compactor-1728931571.gz dest=/data/loki/boltdb-shipper-compactor/index_20010/compactor-1728931571.gz.gz
level=info ts=2024-10-14T19:06:11.15658343Z caller=index_set.go:281 table-name=index_20010 msg="removing source db files from storage" count=2
level=info ts=2024-10-14T19:06:11.157033697Z caller=compactor.go:557 msg="finished compacting table" table-name=index_20010
level=info ts=2024-10-14T19:07:04.891431836Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:07:04.891515202Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:07:04.891553403Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:07:05.021524368Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:07:05.021576435Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:07:05.021587737Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:07:05.021624506Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:08:04.891435314Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:08:04.891524629Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:08:04.89153853Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:08:05.022094402Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:08:05.022150806Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:08:05.022312526Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:08:05.022417263Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:09:04.891791382Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:09:04.891939123Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:09:04.892019404Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:09:05.022068885Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:09:05.022112619Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:09:05.02212298Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:09:05.022132208Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:10:04.891632002Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:10:04.891736097Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:10:04.891769473Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:10:05.021971702Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:10:05.022030756Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:10:05.022040801Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:10:05.022050618Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:10:34.928023015Z caller=checkpoint.go:502 msg="atomic checkpoint finished" old=/data/loki/wal/checkpoint.000016.tmp new=/data/loki/wal/checkpoint.000016
level=info ts=2024-10-14T19:10:34.928419987Z caller=checkpoint.go:573 msg="checkpoint done" time=4m30.025651539s
level=info ts=2024-10-14T19:11:04.890867329Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T19:11:04.890915864Z caller=table_manager.go:252 msg="query readiness setup completed" duration=2.219µs distinct_users_len=0
level=info ts=2024-10-14T19:11:04.891944689Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:11:04.892023901Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:11:04.892039531Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:11:04.902775872Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T19:11:04.903003149Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000017
level=info ts=2024-10-14T19:11:05.022182357Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:11:05.022281589Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:11:05.022315568Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:11:05.022350484Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:12:04.891624242Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:12:04.891728823Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:12:04.891754541Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:12:05.02181Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:12:05.021850078Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:12:05.021860198Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:12:05.021868443Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:13:04.891703935Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:13:04.891799523Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:13:04.891816612Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:13:05.021934809Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:13:05.021982326Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:13:05.021994532Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:13:05.022003889Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:14:04.891668905Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:14:04.891744603Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:14:04.891759968Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:14:05.021886654Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:14:05.02193632Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:14:05.021947227Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:14:05.021957902Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:14:40.942707337Z caller=checkpoint.go:502 msg="atomic checkpoint finished" old=/data/loki/wal/checkpoint.000017.tmp new=/data/loki/wal/checkpoint.000017
level=info ts=2024-10-14T19:14:40.943088269Z caller=checkpoint.go:573 msg="checkpoint done" time=3m36.039828086s
level=info ts=2024-10-14T19:15:04.891950217Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:15:04.892041955Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:15:04.892071651Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:15:05.022156512Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:15:05.022202232Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:15:05.022213801Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:15:05.022241862Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:16:04.891691452Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T19:16:04.89179738Z caller=table_manager.go:252 msg="query readiness setup completed" duration=2.004µs distinct_users_len=0
level=info ts=2024-10-14T19:16:04.891687088Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:16:04.891914528Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:16:04.891964047Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:16:04.902585903Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T19:16:04.902754837Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000018
level=info ts=2024-10-14T19:16:05.021238418Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:16:05.021289944Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:16:05.061197478Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:16:05.06125734Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
ts=2024-10-14T19:16:11.117317532Z caller=spanlogger.go:80 level=info msg="building index list cache"
ts=2024-10-14T19:16:11.117460242Z caller=spanlogger.go:80 level=info msg="index list cache built" duration=74.668µs
level=info ts=2024-10-14T19:16:11.117493721Z caller=compactor.go:552 msg="compacting table" table-name=index_20010
level=info ts=2024-10-14T19:16:11.117588679Z caller=table.go:138 table-name=index_20010 msg="listed files" count=2
level=info ts=2024-10-14T19:16:11.117608264Z caller=table.go:297 table-name=index_20010 msg="starting compaction of dbs"
level=info ts=2024-10-14T19:16:11.117641442Z caller=table.go:307 table-name=index_20010 msg="using compactor-1728932771.gz as seed file"
level=info ts=2024-10-14T19:16:11.119618485Z caller=util.go:116 table-name=index_20010 file-name=compactor-1728932771.gz msg="downloaded file" total_time=1.96603ms
level=info ts=2024-10-14T19:16:11.119910454Z caller=util.go:116 table-name=index_20010 file-name=loki-0-1728928149685619380-1728932400.gz msg="downloaded file" total_time=189.535µs
level=info ts=2024-10-14T19:16:11.130475876Z caller=util.go:136 msg="compressing the file" src=/data/loki/boltdb-shipper-compactor/index_20010/compactor-1728932771.gz dest=/data/loki/boltdb-shipper-compactor/index_20010/compactor-1728932771.gz.gz
level=info ts=2024-10-14T19:16:11.14603889Z caller=index_set.go:281 table-name=index_20010 msg="removing source db files from storage" count=2
level=info ts=2024-10-14T19:16:11.146318798Z caller=compactor.go:557 msg="finished compacting table" table-name=index_20010
level=info ts=2024-10-14T19:17:04.89113065Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:17:04.891278789Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:17:04.891315583Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:17:05.021419458Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:17:05.021468105Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:17:05.021478026Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:17:05.021485982Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:18:04.891323614Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:18:04.891385214Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:18:04.891397805Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:18:05.021589729Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:18:05.021631762Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:18:05.021642916Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:18:05.021652449Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:19:04.891656536Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:19:04.891744994Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:19:04.891761979Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:19:05.022144869Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:19:05.022194261Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:19:05.022204702Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:19:05.022212743Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:19:40.944246366Z caller=checkpoint.go:502 msg="atomic checkpoint finished" old=/data/loki/wal/checkpoint.000018.tmp new=/data/loki/wal/checkpoint.000018
level=info ts=2024-10-14T19:19:40.944593371Z caller=checkpoint.go:573 msg="checkpoint done" time=3m36.041667719s
level=info ts=2024-10-14T19:20:04.891219774Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:20:04.891292087Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:20:04.891438637Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:20:05.021463144Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:20:05.021511409Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:20:05.021523175Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:20:05.021548351Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:21:04.891416813Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:21:04.891700083Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:21:04.891754342Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:21:04.891831665Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T19:21:04.891898892Z caller=table_manager.go:252 msg="query readiness setup completed" duration=1.727µs distinct_users_len=0
level=info ts=2024-10-14T19:21:04.902748907Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T19:21:04.902964983Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000019
level=info ts=2024-10-14T19:21:05.021234117Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:21:05.021298078Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:21:05.021374672Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:21:05.021476378Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:22:04.891409277Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:22:04.891516907Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:22:04.891544983Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:22:05.021545436Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:22:05.021589859Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:22:05.02160074Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:22:05.02161196Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:23:04.891306361Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:23:04.891435913Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:23:04.891502737Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:23:05.021533384Z caller=table_manager.go:134 msg="uploading tables"
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
level=info ts=2024-10-14T19:25:04.89665414Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:25:04.896769174Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:25:04.896785587Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:25:05.022057771Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:25:05.022105633Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:25:05.022118688Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:25:05.02223138Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:25:34.925404603Z caller=checkpoint.go:502 msg="atomic checkpoint finished" old=/data/loki/wal/checkpoint.000019.tmp new=/data/loki/wal/checkpoint.000019
level=info ts=2024-10-14T19:25:34.926055021Z caller=checkpoint.go:573 msg="checkpoint done" time=4m30.022868558s
level=info ts=2024-10-14T19:26:04.891041501Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:26:04.891192964Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:26:04.891306231Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:26:04.891051093Z caller=table_manager.go:213 msg="syncing tables"
level=info ts=2024-10-14T19:26:04.891372143Z caller=table_manager.go:252 msg="query readiness setup completed" duration=1.72µs distinct_users_len=0
level=info ts=2024-10-14T19:26:04.891419037Z caller=table_manager.go:229 msg="cleaning tables cache"
level=info ts=2024-10-14T19:26:04.902999716Z caller=checkpoint.go:615 msg="starting checkpoint"
level=info ts=2024-10-14T19:26:04.90320986Z caller=checkpoint.go:340 msg="attempting checkpoint for" dir=/data/loki/wal/checkpoint.000020
level=info ts=2024-10-14T19:26:05.02142116Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:26:05.021466235Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:26:05.021477975Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:26:05.021487683Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
ts=2024-10-14T19:26:11.117100673Z caller=spanlogger.go:80 level=info msg="building index list cache"
ts=2024-10-14T19:26:11.11724455Z caller=spanlogger.go:80 level=info msg="index list cache built" duration=81.791µs
level=info ts=2024-10-14T19:26:11.117297952Z caller=compactor.go:552 msg="compacting table" table-name=index_20010
level=info ts=2024-10-14T19:26:11.117418321Z caller=table.go:138 table-name=index_20010 msg="listed files" count=1
level=info ts=2024-10-14T19:26:11.117504057Z caller=compactor.go:557 msg="finished compacting table" table-name=index_20010
level=info ts=2024-10-14T19:27:04.891917059Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:27:04.892003519Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:27:04.892039148Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:27:05.022230886Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:27:05.022282003Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:27:05.022293707Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:27:05.022305112Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:28:04.893635042Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:28:04.89372811Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:28:04.893756181Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:28:05.021479693Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:28:05.021539794Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:28:05.021551741Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:28:05.021563309Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"
level=info ts=2024-10-14T19:29:04.891795166Z caller=table_manager.go:167 msg="handing over indexes to shipper"
level=info ts=2024-10-14T19:29:04.891880946Z caller=table.go:319 msg="handing over indexes to shipper index_20010"
level=info ts=2024-10-14T19:29:04.891917631Z caller=table.go:335 msg="finished handing over table index_20010"
level=info ts=2024-10-14T19:29:05.021924596Z caller=table_manager.go:134 msg="uploading tables"
level=info ts=2024-10-14T19:29:05.021990915Z caller=index_set.go:86 msg="uploading table index_20010"
level=info ts=2024-10-14T19:29:05.022056916Z caller=index_set.go:107 msg="finished uploading table index_20010"
level=info ts=2024-10-14T19:29:05.022074303Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20010"


It seems you're asking if the configuration for `auth_enabled: false` is included in your Loki setup. By default, Loki does not enable authentication unless explicitly configured.

In your setup, you can check the configuration files (usually located in the `config.yaml` or similar Loki configuration file) to ensure that this setting is included. Here’s an example of how you can set it:

```yaml
auth_enabled: false
```

This line would be added under the appropriate section (usually `server:` or globally) depending on your setup. If this line is present, then authentication is disabled for your Loki instance. If it's missing, Loki may use default behavior, which could vary depending on your deployment.

Make sure to review your Loki configuration file to confirm the presence of `auth_enabled: false`. You can also add it if you want to disable authentication explicitly.

Let me know if you need further help with your configuration!