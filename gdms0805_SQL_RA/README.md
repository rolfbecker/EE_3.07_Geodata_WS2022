# 1. Install PostgreSQL #

**PostgreSQL** is the most advanced open source object relational database management system (ORDBMS).
<br>Download and install it from [www.postgresql.org](https://www.postgresql.org/)

**psql** is a terminal-based front-end to PostgreSQL (command line interface, CLI) and comes with the installation. 

Additionally the GUI based admin tool **pgAdmin4** will be used.
<br>Download and install it from [www.pgadmin.org](https://www.pgadmin.org/)

# 2. Install Conda environment # 

Install the following packages in our standard `geo` environment: `sqlalchemy psycopg2 pgspecial ipython-sql` 

See [README_SQL_to_be_installed.txt](./README_SQL_to_be_installed.txt)

# 3. Environmental database setup #

Our first database for training is `env_db`. Most of the data we will store is related to environmental science, hence the name `env_db`. It is a relational database (RDB) running on the ORDBMS PostgreSQL.


## Create users and database for environmental monitoring applications ##

Create new users and a new database which we will use for first exercises to get used to SQL and relational algebra (RA). Later we will use the setup to manage environmental data. The environmental database is named `env_db` and the related users `env_master` and `env_user`, respectively.

Open a command window to execute **psql**. On Windows you can run `cmd` or open the *Anaconda Powershell Prompt* (if Anaconda is installed). On Linux or Mac OS just open a terminal window.

**Change to the subdirectory with the SQL scripts**, i.e [./sql_scripts/](./sql_scripts/). The SQL scripts have the extension \*.sql.
<br>Read the code in the scripts. Open the scripts in your favorite editor.

**Change and remember the passwords in the SQL script** creating the users: [./sql_scripts/010_create_users_for_env_db_V001.sql](./sql_scripts/010_create_users_for_env_db_V001.sql)

Be sure you know the host your postgres database resides on (e.g. localhost) and the password of user postgres.

Create new database users connect as (U)ser postgres (superuser) to the maintence (d)atabase postgres by executing

	psql -h localhost -U postgres -d postgres -f 010_create_users_for_env_db_V001.sql

The command line options define: `-h` host (i.e. the server the DB is running on), `-U` user (postgres is the DB superuser), `-d` database (postgres is name of the maintenance database), and `-f` the file with the SQL commands to be executed.

Create the new database `env_db` using the script [./sql_scripts/020_create_database_env_db_V001.sql](./sql_scripts/020_create_database_env_db_V001.sql):

	psql -h localhost -U postgres -d postgres -f 020_create_database_env_db_V001.sql

# 4. Create the example relations used in RA presentation #

In the presentation on Relational Algebra (RA) several relations are used to demonstrate the different operations.  

Admittedly, this example data is not environmental data but it helps to introduce the concepts of RA.

Use the new DB user `env_master` to create the tables (relations) in the new database `env_db` used for the first exercises.

## Create tables "Bar" and "Sells"

Have a look at the SQL script [./sql_scripts/030_create_bars_exercise_tables_and_insert_V001.sql](./sql_scripts/030_create_bars_exercise_tables_and_insert_V001.sql). creating the tables for the _bar example_ of the RA presentation. Execute:

	psql -h localhost -U env_master -d env_db -f 030_create_bars_exercise_tables_and_insert_V001.sql


## Create tables "R", "S", "R1", "R2"

The following script [./sql_scripts/040_create_relations_exercise_tables_and_insert_V001.sql](./sql_scripts/040_create_relations_exercise_tables_and_insert_V001.sql) creates more tables for the exercises:

	psql -h localhost -U env_master -d env_db -f 040_create_relations_exercise_tables_and_insert_V001.sql

