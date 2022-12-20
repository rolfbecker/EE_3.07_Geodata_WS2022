# Database Nomalization #

In the presentation the database for the fictive "For Ladies" sales company is discussed. The spreadsheet "For_Ladies_DB_Normalization_V001.xlsx" in the repo shows the decomposition (normalization) of the initial relation. 
 
The music database example of the **presentation** [DB_NF_normalization_2021-12-13_V002_RB.pdf](./presentation/DB_NF_normalization_2021-12-13_V002_RB.pdf) can be created by the sql script **[070_create_and_fill_music_db_with_music_user_V001.sql](./sql_scripts/070_create_and_fill_music_db_with_music_user_V001.sql)** in the folder sql_scripts.

You can create the database on your PostgreSQL server (probably your localhost, i.e. "your computer") by using the CLI `psql`:

```
psql -U postgres -d postgres -h localhost -p 5432 -f 070_create_and_fill_music_db_with_music_user_V001.sql
```

You could check the reuslts e.g. in `pgadmin4`. It should show now the new database `music_db`with the two new users `music_master` (the music_db owner with superuser rights) and `music_user. 

