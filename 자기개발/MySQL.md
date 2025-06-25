# Day 1: MySQL이란? 데이터베이스의 기본 개념 🗄️

> **MySQL 30일 마스터 시리즈의 첫 번째 이야기**  
> 오늘부터 30일 동안 MySQL을 완전히 정복해보는 여정을 시작합니다!

## 🤔 왜 MySQL을 배워야 할까?

현대의 모든 애플리케이션은 데이터를 다룹니다. 사용자 정보, 게시글, 주문 내역, 로그 데이터... 이 모든 것을 체계적으로 저장하고 관리하는 것이 바로 **데이터베이스**의 역할입니다.

MySQL은 전 세계에서 가장 널리 사용되는 오픈소스 관계형 데이터베이스입니다. 페이스북, 유튜브, 넷플릭스 등 우리가 매일 사용하는 서비스들이 모두 MySQL을 사용하고 있죠.

## 📚 MySQL이란 무엇인가?

### MySQL의 정의

**MySQL**은 Oracle Corporation에서 개발한 **관계형 데이터베이스 관리 시스템(RDBMS)**입니다.

- **My**: 공동 창립자 Michael Widenius의 딸 이름
- **SQL**: Structured Query Language (구조화된 쿼리 언어)

### MySQL의 특징

#### ✅ 장점

- **무료 오픈소스**: 상업적 용도로도 무료 사용 가능
- **높은 성능**: 대용량 데이터 처리에 최적화
- **크로스 플랫폼**: Windows, Linux, macOS 모두 지원
- **풍부한 생태계**: 다양한 도구와 라이브러리 지원
- **쉬운 학습**: 상대적으로 간단한 문법과 직관적인 구조

#### ⚠️ 단점

- **복잡한 쿼리 처리**: PostgreSQL 대비 일부 고급 기능 부족
- **트랜잭션 격리**: 기본 설정에서는 완전한 ACID 지원 한계

## 🏗️ 관계형 데이터베이스(RDBMS)의 핵심 개념

### 1. 테이블(Table)

데이터를 행(Row)과 열(Column)로 구성된 표 형태로 저장

sql

```sql
-- 사용자 테이블 예시
+----+----------+------------------+------------+
| id | name     | email            | created_at |
+----+----------+------------------+------------+
| 1  | 홍길동   | hong@example.com | 2024-01-01 |
| 2  | 김철수   | kim@example.com  | 2024-01-02 |
+----+----------+------------------+------------+
```

### 2. 스키마(Schema)

데이터베이스의 구조와 제약 조건을 정의하는 설계도

### 3. 관계(Relationship)

테이블 간의 연결을 통해 데이터의 중복을 줄이고 일관성을 유지

## 🔍 MySQL vs 다른 데이터베이스 비교

|특징|MySQL|PostgreSQL|SQLite|
|---|---|---|---|
|**성능**|⭐⭐⭐⭐⭐|⭐⭐⭐⭐|⭐⭐⭐|
|**확장성**|⭐⭐⭐⭐|⭐⭐⭐⭐⭐|⭐⭐|
|**학습 난이도**|⭐⭐⭐|⭐⭐⭐⭐|⭐⭐|
|**커뮤니티**|⭐⭐⭐⭐⭐|⭐⭐⭐⭐|⭐⭐⭐|
|**사용 사례**|웹 서비스, 중소규모|대규모 엔터프라이즈|모바일 앱, 임베디드|

## 🛠️ MySQL 설치하기

### Windows 설치

1. [MySQL 공식 사이트](https://dev.mysql.com/downloads/) 접속
2. MySQL Community Server 다운로드
3. MySQL Installer 실행
4. Developer Default 선택하여 설치

### macOS 설치 (Homebrew)

bash

```bash
# Homebrew 설치 (없는 경우)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# MySQL 설치
brew install mysql

# MySQL 서비스 시작
brew services start mysql
```

### Linux (Ubuntu) 설치

bash

```bash
# 패키지 업데이트
sudo apt update

# MySQL 설치
sudo apt install mysql-server

# MySQL 보안 설정
sudo mysql_secure_installation
```

## 🎯 첫 번째 실습: 데이터베이스 생성하기

MySQL이 설치되었다면, 이제 첫 번째 데이터베이스를 만들어보겠습니다!

### 1. MySQL 접속

bash

```bash
mysql -u root -p
```

### 2. 데이터베이스 생성

sql

```sql
-- 새로운 데이터베이스 생성
CREATE DATABASE my_first_db;

-- 생성된 데이터베이스 확인
SHOW DATABASES;

-- 데이터베이스 사용
USE my_first_db;
```

### 3. 첫 번째 테이블 생성

sql

```sql
-- 사용자 테이블 생성
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 테이블 구조 확인
DESCRIBE users;
```

### 4. 데이터 입력해보기

sql

```sql
-- 사용자 데이터 추가
INSERT INTO users (name, email) VALUES 
('홍길동', 'hong@example.com'),
('김철수', 'kim@example.com'),
('이영희', 'lee@example.com');

-- 데이터 조회
SELECT * FROM users;
```

## 🎯 실습 결과 확인

위 코드를 실행하면 다음과 같은 결과를 볼 수 있습니다:

```
+----+--------+------------------+---------------------+
| id | name   | email            | created_at          |
+----+--------+------------------+---------------------+
|  1 | 홍길동 | hong@example.com | 2024-06-10 12:00:00 |
|  2 | 김철수 | kim@example.com  | 2024-06-10 12:00:01 |
|  3 | 이영희 | lee@example.com  | 2024-06-10 12:00:02 |
+----+--------+------------------+---------------------+
```

## 🚀 오늘의 핵심 포인트

1. **MySQL은 세계에서 가장 인기 있는 오픈소스 RDBMS**
2. **관계형 데이터베이스는 테이블 간의 관계로 데이터를 구조화**
3. **MySQL은 웹 서비스 개발에 최적화된 데이터베이스**
4. **CREATE DATABASE로 데이터베이스, CREATE TABLE로 테이블 생성**

## 🤝 미션: 나만의 데이터베이스 만들기

오늘의 과제는 **자신만의 데이터베이스를 설계**하는 것입니다!

### 미션 내용

1. 관심 있는 주제(도서관, 쇼핑몰, 블로그 등)를 선택
2. 해당 주제에 필요한 데이터베이스와 테이블 1개 생성
3. 최소 3개의 컬럼과 5개의 샘플 데이터 입력

### 예시: 도서관 시스템

sql

```sql
CREATE DATABASE library_system;
USE library_system;

CREATE TABLE books (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(200) NOT NULL,
    author VARCHAR(100) NOT NULL,
    isbn VARCHAR(13) UNIQUE,
    published_year INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## 🔗 다음 시간 예고

**Day 2**에서는 **데이터베이스와 테이블 생성**을 더 깊이 있게 다뤄보겠습니다!

- 다양한 CREATE TABLE 옵션들
- 제약 조건(Constraints) 설정
- 실제 프로젝트에서 사용하는 테이블 설계 패턴

---

## 💬 댓글로 소통해요!

- MySQL 설치 중 어려운 점이 있으셨나요?
- 어떤 주제의 데이터베이스를 만들어보셨나요?
- 다음에 다뤘으면 하는 MySQL 주제가 있다면 알려주세요!

**#MySQL #데이터베이스 #RDBMS #개발공부 #30일챌린지**