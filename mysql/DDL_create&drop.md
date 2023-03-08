# Basic DDL

## MySQL DB

- CREATE
    - db 생성

```sql
CREATE DATABASE temp_db;

```

- SHOW
    - 모든 db를 나열

```sql
SHOW DATABASES;
```

![CleanShot 2023-03-07 at 10.21.06.png](Basic%20DDL%20406d290d6df44b13a9add2095d910d35/CleanShot_2023-03-07_at_10.21.06.png)

- USE
    - 특정 DB를 사용하기 위해 USE문을 사용하여 선언
    - USE문을 사용하지 않았을 경우
        - SELECT * FROM *dbname.columnname*;
    - USE문으로 특정 DB를 선택하였을 경우
        - SELECT * FROM *columnname*;

```sql
SELECT * FROM employees;
```

![CleanShot 2023-03-07 at 10.12.43.png](Basic%20DDL%20406d290d6df44b13a9add2095d910d35/CleanShot_2023-03-07_at_10.12.43.png)

```sql
# employees 라는 DB에서 employees 테이블 호출
SELECT * FROM employees.employees;
```

![CleanShot 2023-03-07 at 10.15.40.png](Basic%20DDL%20406d290d6df44b13a9add2095d910d35/CleanShot_2023-03-07_at_10.15.40.png)

- SHOW TABLE STATUS

```sql
USE employees;
SHOW TABLE STATUS;
```

![CleanShot 2023-03-07 at 10.17.37.png](Basic%20DDL%20406d290d6df44b13a9add2095d910d35/CleanShot_2023-03-07_at_10.17.37.png)

- DROP
    - 해당 DB를 삭제

```sql
DROP temp_df;
SHOW DATABASES;
```

![CleanShot 2023-03-07 at 10.21.48.png](Basic%20DDL%20406d290d6df44b13a9add2095d910d35/CleanShot_2023-03-07_at_10.21.48.png)