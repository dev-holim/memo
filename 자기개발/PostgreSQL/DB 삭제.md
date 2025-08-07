```sql
drop database {db명};
```

다음과 같이 세션이 남아있다고 하는 에러가 발생
>new-erp> drop database users
 [2025-08-07 08:28:37] [55006] ERROR: database "{db명}" is being accessed by other users
 [2025-08-07 08:28:37] Detail: There are 2 other sessions using the database.

- 세션 확인
```sql
SELECT pid, usename, application_name, client_addr, backend_start, state  
FROM pg_stat_activity  
WHERE datname = '{db명}';
```

- 세션 강제 종료
```sql
SELECT pg_terminate_backend(pid)  
FROM pg_stat_activity  
WHERE datname = '{db명}';
```
