# Backend Developer

동시성, 조회 성능, 인증과 보안 등 서비스 안정성 문제를 데이터와 테스트로 검증하며 개선해 온 백엔드 개발자입니다.

Java / Spring Boot와 Python / FastAPI로 REST API, 트랜잭션 경계, 비동기 처리 흐름을 구현했습니다.
DEKK에서는 동시 저장, 반복 조회, 관리자 인증 문제를 코드와 테스트로 확인하고 개선했습니다.
쿠팡에서 주 3회 SQL / Excel 기반 리포트를 발행하며 데이터로 근거를 세우는 훈련을 했고, 이 습관은 개발에서도 로그와 테스트로 문제를 검증하는 방식으로 이어지고 있습니다.

## Tech Stack

**Backend**

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white)
![JPA](https://img.shields.io/badge/JPA-59666C?style=flat-square&logo=hibernate&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)

**Database / Cache**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Redisson](https://img.shields.io/badge/Redisson-B71C1C?style=flat-square&logo=redis&logoColor=white)

**AI / ML**

![Faster-Whisper](https://img.shields.io/badge/Faster--Whisper-111827?style=flat-square)
![mDeBERTa-v3](https://img.shields.io/badge/mDeBERTa--v3-7C3AED?style=flat-square)
![Transformers](https://img.shields.io/badge/Transformers-FFD21E?style=flat-square)
![llama.cpp](https://img.shields.io/badge/llama.cpp-111827?style=flat-square)
![EXAONE 3.0](https://img.shields.io/badge/EXAONE_3.0-5B21B6?style=flat-square)

**Infra / Ops**

![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Docker Compose](https://img.shields.io/badge/Docker_Compose-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![GCP](https://img.shields.io/badge/GCP-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![CodeDeploy](https://img.shields.io/badge/CodeDeploy-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![Loki](https://img.shields.io/badge/Loki-F5A800?style=flat-square&logo=grafana&logoColor=white)

**Testing**

![JUnit 5](https://img.shields.io/badge/JUnit_5-25A162?style=flat-square&logo=junit5&logoColor=white)
![Mockito](https://img.shields.io/badge/Mockito-78A641?style=flat-square)

## Featured Projects

### [DEKK - 패션 카드 탐색 및 공유 덱 서비스](https://github.com/potenup-dekk/DEKK-BE)

코디 카드를 스와이프해 취향을 탐색하고 덱에 저장하며, 공유 덱을 함께 편집하고 상품 정보와 구매 링크까지 확인하는 서비스입니다.

원티드랩 포텐업 Final Project 전체 1위 / (2026.02 - 2026.04) / 4인 팀 / Backend

Stack: Java 21, Spring Boot 3, Spring Security, JPA, PostgreSQL, Redis, Redisson, AWS

- 덱(카드 보관함)과 공유 편집 API, 관리자 인증, AWS 백엔드 배포 흐름 담당
- 공유 덱 동시 저장에서 50장 제한과 중복 저장 규칙이 깨질 수 있어 SpEL 기반 `@DistributedLock` AOP와 `REQUIRES_NEW` 트랜잭션을 적용하고, 동시 요청 테스트로 규칙 유지 확인
- 덱 목록의 카드 수와 최신 카드 반복 조회를 일괄 조회로 바꿔 N + N회 쿼리를 1 + 1회로 개선
- 로그아웃과 계정 정지 뒤 기존 JWT를 Redis 차단 목록과 계정 상태 검사로 즉시 거부

### [LearnFlow - AI 영상 요약 학습 플랫폼](https://github.com/team-Octave/learnflow-api)

강사가 강의와 레슨을 등록하고 학습자가 강의를 탐색해 수강하며, 영상 레슨은 수강 전에 AI 요약을 확인하고 수강 후 진도와 리뷰를 관리하는 학습 플랫폼입니다.

(2025.12 - 2026.02) / 7인 팀 / Backend

Stack: Java 21, Spring Boot 3, JPA, MySQL, GCP, GCS, GitHub Actions, Loki

- 강의 승인과 AI 요약 작업 등록, 리뷰 API, GCP 배포와 로그 추적 담당
- 승인 응답 지연과 AI 작업 누락을 막기 위해 승인 상태와 작업을 `ai_outbox`에 한 트랜잭션으로 저장하고, `lesson_id` 유니크 제약과 `SKIP LOCKED`로 중복 처리 방지
- 실패 작업을 1분, 5분, 60분 뒤 최대 3회 재시도하고, 10분 이상 멈춘 작업은 스케줄러가 다시 처리
- 리뷰 목록의 반복 조회를 ID 집합 일괄 조회와 Map 조립으로 바꾸고, Trace ID로 오류 응답과 Loki 로그를 연결

### [Vench AI - 음성 기반 AI 감정 일기 서비스](https://github.com/voice-journal/vench)

음성으로 하루를 기록하면 AI가 자연스러운 일기와 제목으로 다듬고, 8개 감정 점수와 위로 메시지 및 주간 리포트를 제공하는 서비스입니다.

원티드랩 포텐업 AI Hackathon 전체 1위 / (2026.01) / 3인 팀 / Backend & AI Pipeline

Stack: Python, FastAPI, SQLAlchemy, MySQL, Faster-Whisper, mDeBERTa-v3, llama.cpp, EXAONE 3.0

- Faster-Whisper 음성 인식, mDeBERTa-v3 감정 분석, EXAONE 로컬 LLM 생성과 주간 리포트 구현
- 해커톤 기간과 단일 서버 환경을 고려해 별도 메시지 브로커 대신 FastAPI `BackgroundTasks`를 선택하고, `202 Accepted` 응답과 단계별 `process_message`로 긴 AI 처리 과정을 안내
- 4.4GB EXAONE 3.0 Q4_K_M 모델을 `__new__` 싱글톤으로 한 번만 적재하고, 출력별 생성 설정과 후처리 및 실패 폴백 적용
- 8개 감정 점수를 모두 누적해 주간 리포트를 만들고 Prometheus 사용자, 일기, 감정 지표 구현

## Experience

**Coupang COE Team / Grocery Category Owner** (2024.01 - 2024.12)

- SQL / Excel 기반 주 3회 Buyble 분석 및 리포트 발행
- 데이터 기반 의사결정 경험을 바탕으로 백엔드 개발자로 전향

## Education & Certification

- **한양사이버대학교 컴퓨터공학과 졸업** - 최종 이수 140학점 / 평점 3.93 / 4.5 (2022.03 - 2026.08)
- **생성형 AI 기반 FE/BE 협업과정** - 원티드랩 K-Digital / 120일 / 960시간 (2025.09.15 - 2026.03.20)
- **경기 AI 멤버십 채용연계형 교육** - 한컴 x 퓨리오사AI / 3개월 / 420시간 (진행중) / 입사 일정 협의 가능 (2026.08.10 - 2026.11.06)
- **정보처리기사(필기)** / 실기 준비 중 (2026.08.28)

## Links

- Blog: [velog.io/@ashi0312](https://velog.io/@ashi0312/posts)
- Email: [hahahoho5811@gmail.com](mailto:hahahoho5811@gmail.com)
