# ETL Pipeline

Data ingestion and transformation pipeline from Supabase to PostgreSQL.

## Components
- **DAGs**: Airflow orchestration (product sync, transaction ingestion, feature engineering)
- **Spark Jobs**: PySpark transformations (timestamp parsing, deduplication, normalization)
- **External APIs**: Weather and CPI data fetchers
- **SQL**: Database schemas and migrations

## Data Flow
Supabase (raw CSVs) → Airflow DAG → PySpark → PostgreSQL (clean tables)

## Setup
```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt

copy .env.example .env
# Configure Supabase service_role key

docker-compose up -d
```

## DAGs Schedule
- product_sync: Daily
- transaction_ingestion: Every 6 hours
- feature_engineering: Daily
- demand_aggregation: Daily