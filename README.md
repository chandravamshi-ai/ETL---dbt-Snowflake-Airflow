# ETL - dbt, snowflake, airflow

## setup
- pip install dbt-core
- pip install dbt-snowflake
- create a snowflake account

## step 1
- We will create a warehouse, db.
- Inside db we create schema, tables and  role.
- Grant permission to role to access warehouse and db.

## step 2
Let's create warehouse, db, role
- In snowflake, create a new sql worksheet.
- In snowflake role `accountadmin` is super user. using this we will create warehouse, db, role
```sql
use role accountadmin;

create warehouse dbt_wh with warehouse_size='x-small';
create database dbt_db;
create role dbt_role;
```
- run the sql worksheet.

## step 3
- `show grants on warehouse dbt_wh;`
-  `grant usage on warehouse dbt_wh to role dbt_role;`
- The above command should grant usage permission to warehouse 'dbt_wh' to role 'dbt_role'
- `grant role dbt_role to user chandra;`
- replace chandra with your username in snowflake
- `grant all on database dbt_db to role dbt_role`

## step 4
Now we have created warehouse, db ,role. Lets use our newly created role 'dbt_role'
- `use role dbt_role`
- Let's create schema
- `create schema dbt_db.dbt_schema;`

## step 5 
Initialize dbt project
- `dbt init`
- project name `data_pipeline`
- for db setup profile as snowflake. choose option number with snowflake
- it ask for snowflake details. got to account and use locator
- It asks for user name and password set up
- type all the things we created above for ex type db_wh when it asks for wharehouse etc..,
- treads type 10
