# Hi, I'm Dash 👋

**Python Engineer** building reliable batch and streaming pipelines: from messy source data to tested, modeled tables that people can trust.

## 🛠️ Stack

**Languages:** Python · SQL
**Transformation & Modeling:** dbt · PySpark
**Streaming:** Kafka
**Cloud:** AWS · GCP
**Warehousing:** BigQuery · DuckDB
**Orchestration & CI/CD:** GitHub Actions · Kestra · Docker
**Tooling:** uv · ruff · pytest

## 🚀 Projects

**[Congressional Bill Analytics](https://congressional-bills-analytics.streamlit.app/)**: an end-to-end ELT pipeline that ingests official U.S. Congressional bill data daily, models it into a dbt star schema on DuckDB, and serves a Streamlit dashboard showing how far bills get through Congress and where they stall. Includes data quality tests by dimension, CI, and a fully documented [decisions log](https://app.notion.com/p/Decisions-Log-d5763fb2df3182a99cdc8167b801ee24?source=copy_link).

**🔨 Currently building: [Shopper Behaviour Streaming Pipeline](https://app.notion.com/p/Shopper-Classification-Pipeline-41663fb2df31819a985dd8a1f5b42b71?source=copy_link)**, a real-time pipeline for processing shopper behaviour events.

The goal is to turn a raw, messy e-commerce clickstream (views, cart adds, cart removals, purchases) into fresh, trustworthy shopper-behaviour data within about 10 minutes of each event.

```
replay producer → Pub/Sub → BigQuery (bronze) → dbt every ~10 min (silver → gold) → dashboard
```

Key design decisions:
- **Stream in, micro-batch transform:** events stream in through Pub/Sub; dbt transforms them on a ~10-minute schedule.
- **Medallion layers:** bronze is raw and append-only; silver handles deduplication, late and out-of-order events, and sessionisation; gold holds session- and shopper-level behaviour features.
- **Correctness built in:**
  - Deduplication handles Pub/Sub's at-least-once delivery.
  - Incremental models reprocess a lookback window so late events don't split sessions.
  - All logic runs on event time.
- **Realistic replay:** the producer replays a real dataset (REES46, Nov 2019) with its original event timestamps.
- **Success measured as pipeline metrics:** freshness, correctness, test results and query cost.
- **Live shopper labels as the demo use case:** sessions are labelled while still in progress, and those provisional labels are compared with final ones.

**Tools:** Python · Pub/Sub · BigQuery · dbt · Kestra · Terraform · Docker · DuckDB (for local exploration)

## 🤖 Exploring

**Agentic development:** using AI as part of my engineering workflow, including building reusable skills, orchestrating multiple agents across tasks, and finding where AI speeds up data engineering work without compromising correctness.

## 📫 Connect

[LinkedIn](LINK_TO_LINKEDIN)
