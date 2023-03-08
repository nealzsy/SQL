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

![CleanShot_2023-03-07_at_10 21 06](https://user-images.githubusercontent.com/54128055/223586506-3049d80a-67f6-42ab-bb46-6711847416b3.png)

- USE
    - 특정 DB를 사용하기 위해 USE문을 사용하여 선언
    - USE문을 사용하지 않았을 경우
        - SELECT * FROM *dbname.columnname*;
    - USE문으로 특정 DB를 선택하였을 경우
        - SELECT * FROM *columnname*;

```sql
SELECT * FROM employees;
```

![CleanShot_2023-03-07_at_10 12 43](https://user-images.githubusercontent.com/54128055/223586489-8ff7cb64-e923-4452-b177-5c735ee0e209.png)

```sql
# employees 라는 DB에서 employees 테이블 호출
SELECT * FROM employees.employees;
```

![CleanShot_2023-03-07_at_10 15 40](https://user-images.githubusercontent.com/54128055/223586499-a185abe2-34c7-4868-b0e4-06b84839bfb6.png)

- SHOW TABLE STATUS

```sql
USE employees;
SHOW TABLE STATUS;
```

![CleanShot_2023-03-07_at_10 17 37](https://user-images.githubusercontent.com/54128055/223586503-0878b2b7-0272-4bbf-9839-e8a907958caf.png)

- DROP
    - 해당 DB를 삭제

```sql
DROP temp_df;
SHOW DATABASES;
```

![CleanShot_2023-03-07_at_10 21 48](https://user-images.githubusercontent.com/54128055/223586509-c6a34c1c-d572-4125-b829-504c54f30d31.png)
