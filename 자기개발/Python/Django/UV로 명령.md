```bash
uv run --active manage.py runserver
```

DEBUG=False일 때 정적 파일 세팅 
```
uv run manage.py collectstatic --dry-run
```


```
uv pip freeze > requirements.txt
```


```
uv run python manage.py migrate user --database=users
```

```
uv run python manage.py showmigrations user
```