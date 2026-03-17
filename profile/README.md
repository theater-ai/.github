# 📽️ Theater-AI

영화 산업 관련 시장 조사, 분석, 마케팅 보고서 및 외부 기사 데이터를 통합적으로 질의·탐색하는 RAG-Pipeline 입니다.

<br>

## ⚒️ Tech Stacks

| 레이어 | 기술 |
|---|---|
| Frontend | Vue.js |
| Backend | FastAPI |
| Database | PostgreSQL |

<br>

## 실행 방법

#### 명령어

``` bash
make up
```

#### 서비스 주소
| 서비스 | 주소 |
|---|---|
| 프론트엔드 | http://localhost:8501 |
| 백엔드 API | http://localhost:8080 |
| API 문서 (Swagger) | http://localhost:8080/docs |

<br>

## ⚙️ Setting

#### `.env`

``` .env
# PostgreSQL
POSTGRES_USER=movie_user
POSTGRES_PASSWORD=movie_pass
POSTGRES_DB=moviedb
POSTGRES_PORT=5432
DB_CONTAINER=db

# 컨테이너 이름
BACKEND_CONTAINER=backend
FRONTEND_CONTAINER=frontend

# 포트
BACKEND_PORT=8080
FRONTEND_PORT=8501

# KOBIS Open API 키 (https://www.kobis.or.kr/kobisopenapi 에서 발급)
KOBIS_API_KEY=your_api_key_here
```

#### `Makefile`

``` Makefile
# .env 파일 로드
ifneq (,$(wildcard ./.env))
    include .env
    export
endif

.PHONY: up down build rebuild restart logs logs-backend logs-frontend logs-db logs-vectordb ps up-db scrape test-scraper test-scraper-local embed sh-backend restart-backend rebuild-backend restart-frontend rebuild-frontend flush-db flush-vector flush-all clean fclean

# 1. 서비스 기본 제어
up:
	docker compose up -d

down:
	docker compose down

restart:
	docker compose restart

clean:
	docker compose down --remove-orphans

fclean:
	docker compose down -v --remove-orphans
	docker image prune -af
	docker builder prune -af
```

<br>
