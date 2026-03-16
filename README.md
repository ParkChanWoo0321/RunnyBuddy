# 🏃 Runny Buddy Backend API Documentation

Spring Boot 기반의 러닝 커뮤니티 백엔드 프로젝트입니다. 회원가입부터 게시글, 댓글, 좋아요, 스크랩, 알림, 뱃지까지 다양한 기능을 포함하고 있으며, JWT 기반 인증과 OAuth2 소셜 로그인(Kakao, Google, Naver)을 지원합니다.

---

## 📌 목차

* [기술 스택](#기술-스택)
* [인증 및 보안](#인증-및-보안)
* [기능 요약](#기능-요약)
* [엔티티 관계](#엔티티-관계)
* [API 명세](#api-명세)

  * [회원 인증](#1-회원-인증)
  * [게시글](#2-게시글)
  * [댓글](#3-댓글)
  * [좋아요](#4-좋아요)
  * [스크랩](#5-스크랩)
  * [알림](#6-알림)
  * [뱃지](#7-뱃지)

---

## 🧰 기술 스택

* Java 17
* Spring Boot 3.x
* Spring Security + JWT
* JPA (Hibernate)
* MySQL
* SSE (Server-Sent Events)
* MultipartFile (이미지 업로드)
* Gradle

---

## 🔐 인증 및 보안

* JWT 기반 인증 (AccessToken + RefreshToken)
* 소셜 로그인 성공 시 JWT 자동 발급
* 인증 불필요 경로: `/auth/**`, `/oauth2/**`, `/error`
* 모든 인증 요청에 `Authorization: Bearer {accessToken}` 필요

---

## 📋 기능 요약

| 분류           | 기능                                                              |
| ------------ | --------------------------------------------------------------- |
| Auth         | 회원가입, 로그인, 로그아웃, 소셜 로그인, 닉네임 중복확인, 프로필 변경, 내 정보 조회/수정, 비밀번호 재설정 |
| Post         | 게시글 생성/수정/삭제/조회, 이미지 첨부, 태그 검색, 내가 쓴 글 조회                       |
| Comment      | 댓글 작성/수정/삭제, 대댓글 작성/수정/삭제                                       |
| Like         | 게시글 좋아요 토글, 좋아요 수 조회, 내가 받은 총 좋아요 수, 내가 쓴 글 별 좋아요 수 조회, 좋아요 취소  |
| Scrap        | 스크랩 토글, 스크랩한 게시글 조회, 스크랩 취소                                     |
| Notification | SSE 알림 구독, 전체 알림 조회                                             |
| Badge        | 사용자 뱃지 조회 (좋아요 수 기준 자동 지급)                                      |

---

## 🔗 엔티티 관계 (요약)

* `User` ⟷ `Post` (1\:N)
* `User` ⟷ `Comment` (1\:N)
* `Post` ⟷ `Comment` (1\:N)
* `User` ⟷ `Like`, `Scrap` (1\:N)
* `Post` ⟷ `Like`, `Scrap` (1\:N)
* `Post` ⟷ `PostImage`, `Tag` (1\:N)
* `User` ⟷ `Notification`, `Badge` (1\:N)

---
