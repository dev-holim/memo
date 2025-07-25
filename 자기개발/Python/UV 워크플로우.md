### 데이터 사이언스 프로젝트 템플릿

```bash
# 1. 프로젝트 디렉토리 생성
mkdir ds-project
cd ds-project

# 2. 프로젝트 초기화 및 Python 버전 설정
uv init --package
uv python install 3.11
uv use 3.11

# 3. 데이터 사이언스 핵심 패키지 설치
uv add numpy pandas matplotlib scikit-learn

# 4. 개발 도구 설치
uv add --dev ipython jupyterlab black ruff

# 5. 환경 잠금 및 동기화
uv lock
uv sync

# 6. Jupyter Lab 실행
uv run jupyter lab
```

### 웹 개발 프로젝트 템플릿

```bash
# 1. 프로젝트 생성
mkdir web-project
cd web-project

# 2. 프로젝트 초기화
uv init --package
uv python install 3.12
uv use 3.12

# 3. 웹 프레임워크 및 관련 패키지 설치
uv add "fastapi>=0.104.0" "uvicorn[standard]" sqlalchemy pydantic

# 4. 개발 도구 설치
uv add --dev pytest pytest-cov black ruff

# 5. 환경 잠금 및 동기화
uv lock
uv sync

# 6. 개발 서버 실행
uv run uvicorn src.main:app --reload
```

### 기존 프로젝트 마이그레이션

```bash
# 1. 프로젝트 디렉토리로 이동
cd existing-project

# 2. UV 프로젝트 초기화
uv init

# 3. requirements.txt가 있는 경우 의존성 가져오기
cat requirements.txt | xargs uv add

# 4. 환경 잠금 및 동기화
uv lock
uv sync
```