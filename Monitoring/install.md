
---

### What's Installed by Default?

The chart brings in several sub-charts as dependencies automatically:

* **Alertmanager** — handles alerts (silencing, inhibition, routing)
* **kube-state-metrics** — exposes Kubernetes object metrics
* **prometheus-node-exporter** — exports host-level (node) metrics
* **prometheus-pushgateway** — enables metrics from short-lived jobs to be pushed instead of scraped


This means once you do:

```bash
helm install prometheus prometheus-community/prometheus
```

— these components will also be deployed unless explicitly disabled.


---

### How It Works Under the Hood

In `values.yaml`, you'll see those components listed under `charts/` and with corresponding `enabled: true` flags — meaning they are installed as part of the chart.


---

### What About Exporters?

The chart includes:

* **Node Exporter** — preconfigured for each node via a DaemonSet
* **kube-state-metrics** — deployed as a service
* **Pushgateway** — provided for handling metrics from batch jobs


If you need any **additional or specialized exporters** (e.g., for HAProxy, StatsD, Graphite, custom apps), you'll need to add and configure those manually.


---

### Summary Table

| Component            | Installed by Default? | Notes                                 |
| -------------------- | --------------------- | ------------------------------------- |
| Alertmanager         | Yes                   | Supports alert routing and silencing  |
| Node Exporter        | Yes                   | DaemonSet running on each node        |
| kube-state-metrics   | Yes                   | Exposes cluster and object metrics    |
| Pushgateway          | Yes                   | For short-lived job metrics           |
| Additional exporters | No                    | You must add these manually if needed |

---
