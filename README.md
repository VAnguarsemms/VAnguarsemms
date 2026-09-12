Senior platform engineer focused on ingestion pipelines and data infrastructure.

## Ben Hegmann

I build and operate ingestion systems that move hundreds of millions of events daily through Kafka, Flink, and ClickHouse. I own the full path from schema design to on-call: partitioning strategies, backpressure handling, and retention policies. I prioritize durable writes and replayability over latency, and I accept the operational cost of idempotent reprocessing as the price of correctness.

### 🛠 Tech & Infrastructure

**Core**: `Python`, `Kafka`, `Flink`, `ClickHouse`

**Data**: `Avro`, `Redpanda`, `Iceberg`, `Parquet`

**Infra**: `Docker`, `Kubernetes`, `Terraform`

**Tooling**: `pytest`, `ruff`, `Grafana`, `Prometheus`

### ⚙️ Engineering Areas

- Designing idempotent consumers with exactly-once semantics using Kafka transactions and Flink checkpoints.
- Optimizing ClickHouse schema design — `ReplacingMergeTree` tuning, `ORDER BY` key selection, and partition pruning.
- Building schema evolution pipelines with Avro compatibility checks and registry governance.
- Reducing reprocessing blast radius through partitioned backfills and bounded retry queues.

### 🔭 Current Focus

- Balancing Flink checkpoint frequency against end-to-end latency for high-throughput streams.
- Handling schema registry drift when upstream teams change Avro types without coordination.
- Cutting storage costs by moving cold partitions to Iceberg without breaking real-time queries.
- Improving backpressure detection across Kafka consumer groups using lag metrics and consumer coordinator telemetry.

### 📌 Engineering Notes

- Tests must cover failure modes: partition rebalancing, broker outages, and schema mismatches — happy paths are not enough.
- Keep schema migrations additive and backward-compatible; breaking changes belong in a new topic, not a modified one.
- Use exponential backoff with jitter for retries, but never retry non-idempotent writes without a deduplication key.
- Deployments should be invisible to users; if you need a maintenance window, your architecture is wrong.

### 🧭 How I Work

- Prefer explicit ownership: every queue, topic, and table has a named team responsible for its operational health.
- Design for replay before designing for speed; reprocessing from a checkpoint is the first-class recovery path.
- Automate operational runbooks before they become tribal knowledge.

*Correctness under load is a property of the system, not the code.*