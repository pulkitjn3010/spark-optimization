# Sample Datasets

This directory contains sample datasets used for demonstrating PySpark optimization techniques.

## Dataset Descriptions

### 1. NYC Taxi Data (`yellow_tripdata_2023-09.parquet`)
- **Source**: NYC Taxi & Limousine Commission
- **Description**: Yellow taxi trip records from September 2023
- **Size**: ~1.2GB (compressed)
- **Use Cases**: 
  - Join optimization demonstrations
  - Partition tuning examples
  - Skew handling techniques
  - Performance benchmarking

**Schema**:
- `tpep_pickup_datetime`: Pickup timestamp
- `tpep_dropoff_datetime`: Dropoff timestamp
- `PULocationID`: Pickup location ID
- `DOLocationID`: Dropoff location ID
- `trip_distance`: Trip distance in miles
- `fare_amount`: Fare amount
- `tip_amount`: Tip amount
- `total_amount`: Total amount

### 2. Customer Data (`customers.parquet`)
- **Description**: Synthetic customer information dataset
- **Use Cases**: 
  - Broadcast join examples
  - Small table optimization
  - Lookup table demonstrations

**Schema**:
- `customer_id`: Unique customer identifier
- `name`: Customer name
- `email`: Customer email
- `city`: Customer city
- `state`: Customer state
- `registration_date`: Customer registration date

### 3. Transaction Data (`transactions.parquet`)
- **Description**: Sample transaction records
- **Use Cases**:
  - Join optimization with customer data
  - Aggregation examples
  - Window function demonstrations

**Schema**:
- `transaction_id`: Unique transaction identifier
- `customer_id`: Customer identifier (foreign key)
- `amount`: Transaction amount
- `transaction_date`: Transaction timestamp
- `category`: Transaction category
- `merchant`: Merchant name

## Data Generation

If you need to regenerate or create additional sample data, you can use the following approach:

```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import *
import random
from datetime import datetime, timedelta

# Create sample customer data
customers_data = []
for i in range(10000):
    customers_data.append({
        'customer_id': i,
        'name': f'Customer_{i}',
        'email': f'customer{i}@example.com',
        'city': random.choice(['New York', 'Los Angeles', 'Chicago', 'Houston']),
        'state': random.choice(['NY', 'CA', 'IL', 'TX']),
        'registration_date': datetime.now() - timedelta(days=random.randint(1, 365))
    })

# Create sample transaction data
transactions_data = []
for i in range(100000):
    transactions_data.append({
        'transaction_id': i,
        'customer_id': random.randint(0, 9999),
        'amount': round(random.uniform(10, 1000), 2),
        'transaction_date': datetime.now() - timedelta(days=random.randint(1, 30)),
        'category': random.choice(['Food', 'Shopping', 'Transport', 'Entertainment']),
        'merchant': f'Merchant_{random.randint(1, 100)}'
    })
```

## Data Usage Guidelines

1. **Parquet Format**: All datasets are stored in Parquet format for optimal performance with Spark
2. **Partitioning**: Consider partitioning large datasets by date or category for better performance
3. **Compression**: Parquet files use Snappy compression by default
4. **Schema Evolution**: Parquet supports schema evolution, allowing you to add new columns

## Performance Tips

- Use `spark.read.parquet()` for optimal reading performance
- Consider caching frequently accessed datasets
- Use appropriate partitioning strategies based on your query patterns
- Monitor memory usage when working with large datasets

## Data Privacy

All datasets in this directory are either:
- Publicly available datasets (NYC Taxi data)
- Synthetic data generated for demonstration purposes
- Anonymized sample data

No real customer or transaction data is included in this repository.
