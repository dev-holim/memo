### 배경
easy_install, pip, poetry를 보완하여 만드러짐
Rust로 작성된 **고속 의존성 해석엔진**
가상환경 생성, 의존성관리, python 버전 관리, 패키징, 서드파티 도구 실행 등을 한번에 처리



### 프로젝트 초기화
```bash
uv init example
```

| 명령어                 | 설명                | 생성되는 파일/디렉토리                                        |
| ------------------- | ----------------- | --------------------------------------------------- |
| `uv init`           | 기본 프로젝트 초기화       | `pyproject.toml`, `.python-version`                 |
| `uv init --package` | 패키지 형태 프로젝트 생성    | `pyproject.toml`, `.python-version`,<br>`src/` 디렉토리 |
| `uv init --lib`     | 배포용 라이브러리 프로젝트 생성 | 라이브러리 구조의 `pyproject.toml`, <br>테스트 디렉토리 등          |

### 의존성 관리
- 추가
```bash
# uv add [추가할 라이브러리]==[버전]
uv add ruff==2.2.2
```

- 삭제
```bash
uv remove ruff
```

- 개발용 추가
```bash
uv add ruff --dev
```

- extra `pip install "uvicorn[standard]"`
```bash
uv add uvicorn --extra standard
```

- export `pip install requirements.txt`
```bash
uv export -o requirements.txt
```

### 파이썬 설치 및 관리
```bash
# 설치 가능한 버전 목록 표시
uv python list

# 현재 시스템에서 설치된 Python 탐색
uv python find

# 현재 프로젝트에 특정 버전 고정
uv python pin
```

```bash
uv python install 3.12
```

```bash
uv python install 3.10 3.11 3.12
```

```bash
uv use <버전>
```
### 가상환경 설치
```bash
uv venv .venv
```

```bash
uv venv --python 3.12

uv venv [경로]
uv venv -p 3.12 [경로]

# 현재 프로젝트 설정으로 가상환경 동기화
# (프로젝트 클론 후 환경 재현 시) pyproject.toml과 uv.lock 기반으로 .venv 동기화
uv sync
```


| 기능        | 기존 도구                             | UV                       | UV의 장점               |
| --------- | --------------------------------- | ------------------------ | -------------------- |
| Python 설치 | `pyenv install 3.11`              | `uv python install 3.11` | 빠른 설치, 자동 환경 설정      |
| 가상환경 생성   | `python -m venv .venv`            | `uv venv .venv`          | 10배 이상 빠른 속도         |
| 패키지 설치    | `pip install requests`            | `uv add requests`        | 의존성 자동 관리, 하드 링크 활용  |
| 의존성 고정    | `pip freeze > requirements.txt`   | `uv lock`                | 정확한 의존성 해결, 플랫폼별 최적화 |
| 환경 동기화    | `pip install -r requirements.txt` | `uv sync`                | 빠른 설치, 확실한 재현성       |
| 도구 실행     | `pipx run black .`                | `uvx black .`            | 캐싱 활용, 빠른 실행         |


```bash
# 자세한 로그 출력
uv --verbose add requests

# 캐시 정리
uv cache clean

# 의존성 트리 확인
uv pip show --tree pandas
```