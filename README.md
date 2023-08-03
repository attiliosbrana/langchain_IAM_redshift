# LangChain IAM Redshift Demo

This notebook demonstrates how to connect LangChain to a Redshift database using IAM authentication. Ultimately, a SQLDatabaseChain is used.

## Prerequisites

- An active Redshift cluster with IAM access enabled
- The following Python packages:
    - langchain
    - langchain-experimental
    - SQLAlchemy
    - psycopg2
    - python-dotenv

## Setup

Create a `.env` file in the repo root with your Redshift credentials:

<!---->

Copy code

```bash
HOST=your-cluster.redshift.amazonaws.com
PORT=5439
DATABASE=your_db_name 
DB_USER=your_iam_user
PASSWORD=your_password 
LOGIN_URL=https://your-sso-url.awsapps.com/start#/
CLUSTER_IDENTIFIER=your_cluster_id 
REGION=your_aws_region
```

## Usage

The notebook shows an example of:

- Loading credentials from `.env`
- Constructing a SQLAlchemy engine URL with IAM params
- Instantiating a LangChain SQLDatabase from the engine
- Creating a SQLDatabaseChain with a language model
- Querying the database through the chain

The chain has query checking enabled to catch errors.

Currently the notebook just runs a simple `COUNT(*)` query against the information schema to test the connection. You can modify it to run queries against your actual tables.

Let me know if any part of the README needs more explanation!