# Docker Containers – PostgreSQL + Python App

This project demonstrates a simple multi-container application using Docker and Docker Compose.  
It runs a PostgreSQL database seeded with sample trip data and a Python application that connects to the database, runs analytical queries, computes basic statistics, and outputs the results to both the console and a JSON file.

---

## 📦 Stack Overview

**Service 1 – PostgreSQL**
- Runs PostgreSQL 16 in a container
- Automatically initializes a `trips` table using an SQL script
- Seeds the table with sample trip data

**Service 2 – Python App**
- Lightweight Python 3.11 container
- Connects to Postgres using environment variables
- Executes read-only queries
- Computes summary statistics
- Writes results to `/out/summary.json` and prints them to stdout

---

## 📁 Project Structure

```text
.
├── app/
│   ├── Dockerfile
│   └── main.py
├── db/
│   ├── Dockerfile
│   └── init.sql
├── out/
├── compose.yml
├── Makefile
├── .env
└── README.md
```
## ⚙️ Environment Configuration
```text
POSTGRES_USER=<appuser>
POSTGRES_PASSWORD=<secretpw>
POSTGRES_DB=<dbname>

DB_HOST=db
DB_PORT=<5432>
DB_USER=<appuser>
DB_PASS=<secretpw>
DB_NAME=<dbname>

APP_TOP_N=10
```
## How to Run
create a .env based on above sample

-Using command
```
docker compose up --build

```
-Using Makefile

```
make

```

## Output

- Results are written to: out/summary.json
