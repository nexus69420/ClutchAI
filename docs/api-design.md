# 🔌 API Design


## Overview


ClutchAI backend exposes REST APIs using FastAPI.


The API layer handles:

- users
- matches
- analytics
- AI coaching


---

# API Structure


```text
/api/v1

├── auth

├── users

├── matches

├── analytics

├── coach
```


---

# Authentication


## Register User


POST


```text
/api/v1/auth/register
```


Body:


```json
{
    "username":"player",
    "email":"user@email.com",
    "password":"password"
}
```


---


## Login


POST


```text
/api/v1/auth/login
```


Returns:


```json
{
    "access_token":"jwt_token"
}
```


---

# Player API


## Get Player Profile


GET


```text
/api/v1/users/profile
```


Response:


```json
{
    "rank":"Diamond",
    "main_role":"Entry",
    "matches":120
}
```


---

# Match API


## Sync Matches


POST


```text
/api/v1/matches/sync
```


Process:


```text
Game API

|

Backend

|

Database
```


---

# Analytics API


## Get Performance Report


GET


```text
/api/v1/analytics/report
```


Response:


```json
{
    "aim_score":85,
    "consistency":70,
    "weakness":"aggression"
}
```


---

# AI Coach API


## Ask Coach


POST


```text
/api/v1/coach/chat
```


Input:


```json
{
    "message":
    "Why am I losing games?"
}
```


Output:


```json
{
    "response":
    "Your attack rounds show low entry success."
}
```


---

# Background Jobs


Long tasks use workers.


Examples:


- match syncing
- ML processing
- AI reports


Flow:


```text
API Request

|

Redis Queue

|

Worker

|

Database Update
```


---

# API Principles


- Async first
- Typed schemas
- JWT security
- Versioned APIs
- Clean responses
