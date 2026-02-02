# pet_project_scd2
pet_project_scd2
Pet project for working with SCD2 type data in a data warehouse.

Создание виртуального окружения
python3.12 -m venv venv && \
source venv/bin/activate && \
pip install --upgrade pip && \
pip install poetry && \
poetry lock && \
poetry install

CREATE SCHEMA stg;

CREATE SCHEMA raw;
DROP TABLE IF EXISTS raw.raw_users;
CREATE TABLE raw.raw_users (
	id uuid NULL,
	created_at timestamp NULL,
	updated_at timestamp NULL,
	first_name text NULL,
	last_name text NULL,
	middle_name text NULL,
	birthday date NULL,
	email text NULL,
	ts_db timestamp NULL
);

CREATE SCHEMA ods;
DROP TABLE IF EXISTS ods.dim_users;
CREATE TABLE ods.dim_users (
	id uuid PRIMARY KEY,
	created_at timestamp NULL,
	updated_at timestamp NULL,
	first_name text NULL,
	last_name text NULL,
	middle_name text NULL,
	birthday date NULL,
	email text NULL
);

CREATE SCHEMA dds;
DROP TABLE IF EXISTS dds.dim_scd2_users;
CREATE TABLE dds.dim_scd2_users (
	id uuid,
	created_at timestamp NULL,
	updated_at timestamp NULL,
	first_name text NULL,
	last_name text NULL,
	middle_name text NULL,
	birthday date NULL,
	email text NULL,
	actual_from timestamp NULL,
	actual_to timestamp NULL,
	ts_db timestamp NULL
);