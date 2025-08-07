```sql
SELECT setval('staff_id_seq', (SELECT MAX(id) FROM staff));

SELECT setval('staff_id_seq', 1, false);
```

