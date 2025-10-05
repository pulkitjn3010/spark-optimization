# Sample Datasets

This directory contains sample datasets used for demonstrating PySpark optimization techniques.

## Dataset Descriptions

**Parquet Format**: All datasets are stored in Parquet format for optimal performance with Spark

### 1. **Customer Data** (`customers.parquet`)

* **Size**: 156 KB
* **Description**: Synthetic dataset containing customer demographic and location details.

#### **Schema**

| Column Name | Type   | Description                     |
| ----------- | ------ | ------------------------------- |
| `cust_id`   | string | Unique customer identifier      |
| `name`      | string | Customer’s full name            |
| `age`       | string | Customer’s age                  |
| `gender`    | string | Gender of the customer          |
| `birthday`  | string | Date of birth of the customer   |
| `zip`       | string | Customer ZIP/postal code        |
| `city`      | string | City where the customer resides |

#### **Sample Data**

| cust_id    | name          | age | gender | birthday   | zip   | city        |
| ---------- | ------------- | --- | ------ | ---------- | ----- | ----------- |
| C007YEYTX9 | Aaron Abbott  | 34  | Female | 7/13/1991  | 97823 | boston      |
| C00B971T1J | Aaron Austin  | 37  | Female | 12/16/2004 | 30332 | chicago     |
| C00WRSJF1Q | Aaron Barnes  | 29  | Female | 3/11/1977  | 23451 | denver      |
| C01AZWQMF3 | Aaron Barrett | 31  | Male   | 7/9/1998   | 46613 | los_angeles |
| C01BKUFRHA | Aaron Becker  | 54  | Male   | 11/24/1979 | 40284 | san_diego   |

---

### 2. **Transaction Data** (`transactions.parquet`)

* **Size**: 870 MB
* **Description**: Synthetic dataset containing customer transaction details such as spending type, location, and amount.
* **Use Cases**:

  * Join and aggregation examples
  * Partitioning and bucketing demonstrations
  * Delta Lake optimization experiments

#### **Schema**

| Column Name    | Type   | Description                                              |
| -------------- | ------ | -------------------------------------------------------- |
| `cust_id`      | string | Customer identifier (foreign key)                        |
| `start_date`   | string | Customer’s account start date                            |
| `end_date`     | string | Account closing or last active date                      |
| `txn_id`       | string | Unique transaction identifier                            |
| `date`         | string | Transaction date                                         |
| `year`         | string | Transaction year                                         |
| `month`        | string | Transaction month                                        |
| `day`          | string | Transaction day                                          |
| `expense_type` | string | Category of the expense (e.g., Groceries, Entertainment) |
| `amt`          | string | Transaction amount                                       |
| `city`         | string | City where the transaction occurred                      |

#### **Sample Data**

| cust_id    | start_date | end_date   | txn_id          | date       | year | month | day | expense_type  | amt    | city        |
| ---------- | ---------- | ---------- | --------------- | ---------- | ---- | ----- | --- | ------------- | ------ | ----------- |
| C0YDPQWPBJ | 2010-07-01 | 2018-12-01 | TZ5SMKZY9S03OQJ | 2018-10-07 | 2018 | 10    | 7   | Entertainment | 10.42  | boston      |
| C0YDPQWPBJ | 2010-07-01 | 2018-12-01 | TYIAPPNU066CJ5R | 2016-03-27 | 2016 | 3     | 27  | Motor/Travel  | 44.34  | portland    |
| C0YDPQWPBJ | 2010-07-01 | 2018-12-01 | TETSXIK4BLXHJ6W | 2011-04-11 | 2011 | 4     | 11  | Entertainment | 3.18   | chicago     |
| C0YDPQWPBJ | 2010-07-01 | 2018-12-01 | TQKL1QFJY3EM8LO | 2018-02-22 | 2018 | 2     | 22  | Groceries     | 268.97 | los_angeles |
| C0YDPQWPBJ | 2010-07-01 | 2018-12-01 | TYL6DFP09PPXMVB | 2010-10-16 | 2010 | 10    | 16  | Entertainment | 2.66   | chicago     |

---
