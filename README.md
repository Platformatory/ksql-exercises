# KSQL Stream Processing

## Background

There are 2 input topics for product(3 partitions) and purchase(6 partitions) information respectively. The product information is retreived from a postgres database. The purchase information is through a datagen source connector with JSON convertor.

## Setup

1. Setup a datagen source connector with the schema defined in [purchase-schema.json](./purchase-schema.json)
2. Setup the database and the load the database with the [docker-compose.yaml](./docker-compose.yaml). Run
```bash
docker-compose up -d --build
```
Check the database contents with
```bash
docker-compose exec -it postgres psql "postgres://platformatory:plf_password@postgres:5432/plf_training"
```
4. Add Kafka, connect and KSQL to the docker-compose file
3. Create a source connector in KSQL for the JDBC Postgres connector.


## Requirements

- Find the top performing product every 5 minutes for the past 1 hour
  - Top performing product = product with highest amount in sales
  - Output should include the amount from sales as well
    - Calculate the amount from purchase by multiplying the quantity with product price and deducting the discount percentage
  - The output should include the product information as well
- The output should be in avro format

[TODO]

- Create a topic with the complete customer purchases details with the following
  - Customer details
  - Product details
  - Purchase details
  - Customer session details


