```bash
jupyter notebook --ip=0.0.0.0 --port=8888 --no-browser
```


1. jupyter 초기 비밀번호 설정
```bash
# jupyter v6 이하
python -c "from notebook.auth import passwd; print(passwd())"

# jupyter v7 이상
python -c "from jupyter_server.auth import passwd; print(passwd())"
```

2. 해시값 복사
```bash
Enter password:
Verify password:
argon2:$argon2id$v=19$...
```

3. 설정파일 생성
```bash
jupyter notebook --generate-config

# ~/.jupyter/jupyter_notebook_config.py 생성
```

4. jupyter_notebook_config.py 수정
```python
c.NotebookApp.password = 'argon2:$argon2id$v=19$gN4... (복사한 해시)'

# 외부접속
c.NotebookApp.ip = '0.0.0.0'
c.NotebookApp.port = 8888
c.NotebookApp.open_browser = False
```

```
argon2:$argon2id$v=19$m=10240,t=10,p=8$TnaSzwU2TQ9WJom9/3pF6w$y/tKXQHUBPrU10hKmX9cCr0xF/5eBwPnOEJ6vez+vk8
```