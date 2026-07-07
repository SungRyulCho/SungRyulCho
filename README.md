# Java/Spring Backend Developer

Java/Spring 기반 백엔드 개발을 중심으로 도메인 정합성, 인증/인가, 트랜잭션 경계, 동시성 제어, 조회 성능 개선을 다룹니다.

서비스 기능을 구현하는 데서 끝내지 않고, 문제가 생기는 지점을 테스트와 지표로 확인한 뒤 코드 구조와 운영 흐름까지 함께 정리하는 개발자를 지향합니다.

## Tech Stack

**Backend**

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white)
![JPA](https://img.shields.io/badge/JPA-59666C?style=flat-square&logo=hibernate&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)

**Database / Cache**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Redisson](https://img.shields.io/badge/Redisson-B71C1C?style=flat-square&logo=redis&logoColor=white)

**AI / Product MVP**

![OpenAI API](https://img.shields.io/badge/OpenAI_API-412991?style=flat-square&logo=openai&logoColor=white)
![STT](https://img.shields.io/badge/STT-374151?style=flat-square)
![Emotion Analysis](https://img.shields.io/badge/Emotion_Analysis-7C3AED?style=flat-square)
![Local LLM](https://img.shields.io/badge/Local_LLM-111827?style=flat-square)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)

**Infra / Test / Ops**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![CodeDeploy](https://img.shields.io/badge/CodeDeploy-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![JUnit](https://img.shields.io/badge/JUnit-25A162?style=flat-square&logo=junit5&logoColor=white)
![k6](https://img.shields.io/badge/k6-7D64FF?style=flat-square&logo=k6&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)

## Featured Projects

### DEKK - 패션 큐레이션 공유 덱 서비스

원티드랩 포텐업 Final Project 전체 1위

Stack: Java, Spring Boot, JPA, PostgreSQL, Redis, Redisson, JWT, AWS

- 보관함/공유 덱 도메인, 카드 저장, 초대/참여/퇴장, 호스트 승계 정책 구현
- 공유 덱 카드 저장의 중복 저장과 50장 제한 초과 가능성을 Redisson 분산 락으로 제어
- `@DistributedLock` AOP와 새 트랜잭션 실행을 분리해 DB commit 이후 unlock 순서 보장
- 덱 목록 최신 카드 반복 조회를 window function 기반 bulk query로 개선
- 동일 500 VUs 기준 평균 응답 시간을 839.44ms에서 552.95ms로 개선
- JWT refresh 401 loop, logout blacklist, 관리자 kick-out, 로그인 실패 제한 흐름 보완

### Emori - 감정카드 기반 소통 MVP

모두의 창업 1차 심사 통과

Stack: Next.js, TypeScript, PostgreSQL, OpenAI, Vercel

- 한국 거주 외국인과 한국인이 하루 공유 음성을 기반으로 감정카드를 교환하는 MVP 설계/구현
- Next.js API Routes로 session, matching, transcription, emotion analysis, card exchange, report API 구성
- OpenAI STT, 번역, 감정 분석 결과를 감정카드 생성 흐름으로 연결
- 무음/불명확 녹음은 임의 카드 생성 대신 재녹음으로 되돌리는 품질 기준 적용
- 관리자 화면에서 신고 검수, 계정 정지, 매칭 관계 정리, OpenAI 비용 추적 기능 구성

### Vench - 음성 기반 AI 감정 일기 서비스

원티드랩 포텐업 AI Hackathon 전체 1위

Stack: Python, FastAPI, SQLAlchemy, MySQL, Streamlit, Docker, Faster-Whisper, Transformers, llama.cpp

- 음성 업로드 이후 STT, 감정 분류, 로컬 LLM 생성을 거쳐 감정 일기와 조언 생성
- 긴 AI 처리 시간을 사용자 요청과 분리하기 위해 `202 Accepted`, background task, 상태 조회 API 구성
- `PENDING`, `PROCESSING`, `COMPLETED`, `FAILED` 상태를 DB에 저장하고 UI polling으로 결과 확인
- 빈 전사, 모델 실패, 처리 예외를 임의 결과로 대체하지 않고 실패 상태와 메시지로 분리
- Docker Compose로 API, UI, DB, 관찰 도구 실행 환경 구성

## Experience

**Coupang COE Team - Grocery Category Owner**

2024.01 - 2024.12

- SQL과 Excel 기반 브랜드별 buyable 분석 리포트 발행
- URL, 카테고리, 중복, 판매 가능 상태 기준으로 상품 데이터 검수
- 재입점 브랜드 데이터 정리로 buyable을 55%에서 88%로 개선

## Study & Current Focus

- 정보처리기사: 소프트웨어공학, DB, 네트워크, 보안 개념 정리 중
- Coding Test: 알고리즘 문제 풀이 기록

## Links

- Blog: [velog.io/@ashi0312](https://velog.io/@ashi0312/posts)
- Email: [hahahoho5811@gmail.com](mailto:hahahoho5811@gmail.com)
