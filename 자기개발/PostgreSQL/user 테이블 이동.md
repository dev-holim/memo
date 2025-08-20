
```sql
-- telepix 계정에서  
CREATE EXTENSION IF NOT EXISTS postgres_fdw WITH SCHEMA test_rdb;  
  
-- terraform(외부 테이블 생성할 database)-- sso database에서 erp 테이블 복사  
CREATE SERVER staff_server  
    FOREIGN DATA WRAPPER postgres_fdw  
    OPTIONS (host '10.0.10.220', dbname 'sso', port '30007');  
  
CREATE USER MAPPING FOR CURRENT_USER  
    SERVER staff_server  
    OPTIONS (user 'telepix', password 'telepix123');  
  
  
IMPORT FOREIGN SCHEMA public  
    LIMIT TO (staff)  
    FROM SERVER staff_server  
    INTO public;  
  
  
DROP EXTENSION IF EXISTS postgres_fdw CASCADE;
```