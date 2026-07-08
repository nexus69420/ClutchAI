# 🧠 ClutchAI

> AI-powered FPS performance analyst that turns raw match statistics into personalized coaching using Machine Learning and Generative AI.

ClutchAI analyzes player performance, detects weaknesses, understands playstyle patterns, and generates improvement plans like a personal esports coach.

---

## 🎯 Problem

Competitive FPS players generate thousands of data points every match:

- kills
- deaths
- assists
- accuracy
- economy
- agents
- maps
- rounds
- play patterns

Existing trackers only show numbers.

They tell you:

"You have 18% headshot rate"

but not:

"Why are you stuck at your rank?"

ClutchAI bridges that gap.

---

# 🚀 Features

## 1. Player Performance Dashboard

Aggregates match history and visualizes:

- Rank progression
- Win rate trends
- Agent performance
- Map weaknesses
- Consistency
- Combat stats


---

## 2. AI Coach Engine

Personalized AI assistant trained on:

- player statistics
- game knowledge
- strategies
- meta updates


Example:

User:

"Why am I losing on attack?"

AI:

"Your entry success rate drops heavily on attack rounds.
You frequently take opening duels without teammate support."


---

## 3. Player Archetype Detection

Machine Learning clustering system.

Detects playstyle:

Examples:

```
70% Entry Duelist
20% Support
10% Lurker
```

Models:

- KMeans
- DBSCAN
- Embedding similarity


---

## 4. Weakness Detection Model


Input:

```
Player Match Features
        |
        v
ML Model
        |
        v
Performance Weakness
```

Detects:

- aim issues
- inconsistency
- poor agent selection
- bad map performance
- aggression problems


Models:

- Random Forest
- XGBoost
- Neural Networks


---

## 5. Personalized Training Generator

Creates improvement quests:

Examples:

Daily Tasks:

- Improve first duel percentage
- Practice specific agents
- Improve consistency score


Generated using LLM reasoning.

---

## 6. RAG Powered Game Knowledge

Knowledge sources:

- agent guides
- maps
- strategies
- patch notes
- professional gameplay analysis


Pipeline:

```
Documents
    |
Chunking
    |
Embeddings
    |
Vector Database
    |
Retrieval
    |
LLM Coach
```


---

# 🏗️ Architecture


```
                 Riot API

                     |
                     v

              FastAPI Backend

                     |

 ------------------------------------------------

 |                     |                         |

ML Service          RAG Engine              Database

 |                     |                         |

Sklearn             Qdrant              PostgreSQL

XGBoost             LangChain            Redis


                     |
                     v


               AI Coach Response


                     |
                     v


              Next.js Frontend

```


---

# 🛠️ Tech Stack


## Frontend

- Next.js
- TypeScript
- TailwindCSS
- shadcn/ui
- Recharts


## Backend

- Python
- FastAPI
- Pydantic
- SQLAlchemy


## Database

- PostgreSQL
- Redis


## Machine Learning

- Pandas
- NumPy
- Scikit-learn
- PyTorch
- XGBoost


## Generative AI

- LangChain
- LangGraph
- Qdrant
- Gemini/OpenAI


## Infrastructure

- Docker
- GitHub Actions
- AWS/GCP


---

# 🧠 ML Pipeline


```
Match History

      |

Feature Engineering

      |

Model Processing

      |

Player Profile


      |

LLM Reasoning


      |

Personalized Coaching

```

---

# Future Roadmap


## Phase 1

✔ Riot API integration  
✔ Dashboard  
✔ AI generated reports


## Phase 2

✔ ML playstyle analysis  
✔ Weakness prediction  
✔ Ranking recommendations


## Phase 3

✔ Gameplay video analysis  
✔ Computer Vision  
✔ VOD reviews


## Phase 4

✔ Desktop overlay assistant  
✔ Real-time coaching



---

# Goal

Build an intelligent coaching platform that explains performance, not just displays statistics.
