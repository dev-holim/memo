# README.md 작성 요령 (프론트엔드 / 백엔드)

## ✅ 공통 README.md 작성 구성 (프론트/백엔드 공통)

1. **프로젝트 이름 및 설명**
   - 간결한 제목
   - 프로젝트의 목적과 핵심 기능 요약

2. **기술 스택**
   - 사용된 언어나 프레임워크, 주요 라이브러리
   - 예: `TypeScript`, `React`, `FastAPI`, `PostgreSQL`, `Redis`, `Docker`

3. **디렉터리 구조 (간단히)**
   ```bash
   📦project-root
   ┣ 📂src
   ┣ 📂public
   ┣ 📂docs
   ┗ 📄README.md
   ```

4. **설치 및 실행 방법**
   ```bash
   # 의존성 설치
   npm install

   # 개발 서버 실행
   npm run dev
   ```

5. **환경 변수 (.env) 설정 예시**
   ```env
   VITE_API_BASE_URL=https://api.example.com
   ```

6. **API 문서 링크 / Swagger UI 경로**
   - `/docs`, `/swagger`, `Postman Collection` 링크 등

7. **배포 관련 정보 (선택)**
   - CI/CD, 배포 서버 주소, 도커 이미지, 헬름 차트 등

8. **기여 방법 / Git 브랜치 전략 (선택)**
   - `main/dev/feature` 브랜치 정책
   - 커밋 메시지 컨벤션 등

9. **작성자 및 연락처 (선택)**

---

## 🟦 프런트엔드 전용 작성 항목

1. **빌드 도구 및 실행 방법**
   ```bash
   # 개발 서버 실행
   npm run dev

   # 프로덕션 빌드
   npm run build
   ```

2. **라우팅 구조 및 페이지 구성**
   ```md
   - `/login` → `LoginPage`
   - `/dashboard` → `DashboardPage`
   ```

3. **상태 관리 도구**
   - Redux, Zustand, Recoil 등 사용 시 설명

4. **디자인 시스템/컴포넌트 라이브러리**
   - 예: TailwindCSS, MUI, Ant Design

5. **API 연동 방식**
   - axios/fetch/React Query 등

6. **모의 데이터/백엔드 서버 연동 방법**
   - Mock API 사용 여부, Swagger 참조 방법 등

---

## 🟧 백엔드 전용 작성 항목

1. **API 서버 실행 방법**
   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   uvicorn main:app --reload
   ```

2. **데이터베이스 연결**
   ```env
   DATABASE_URL=postgresql://user:pass@localhost:5432/dbname
   ```

3. **마이그레이션 도구**
   - Alembic, Django Migrations, Prisma 등

4. **Swagger/OpenAPI 경로**
   - 예: `http://localhost:8000/docs`

5. **테스트 실행 방법**
   ```bash
   pytest tests/
   ```

6. **의존 서비스 정보**
   - Redis, RabbitMQ, Kafka 등 사용 여부와 포트

---

## 📌 작성 팁

- 마크다운 형식(헤딩, 코드블록, 목록 등)을 적극 활용
- 최신 정보를 유지하도록 팀 내 문서 책임자 지정 권장
- 사내 환경(DNS, VPN 등)과 연계되는 경우 주석 또는 대체 설명 추가
