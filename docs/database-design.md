# 🗄️ ClutchAI Database Design


## Overview


ClutchAI uses multiple storage systems depending on data type.


Databases:


```text
PostgreSQL

    +

Redis

    +

Qdrant
```


Each database solves a different problem.


---

# Database Responsibilities


## PostgreSQL


Stores structured application data.


Examples:

- users
- matches
- player statistics
- analytics
- ML outputs
- reports


---

## Redis


High speed temporary storage.


Used for:

- caching
- background queues
- sessions
- rate limits


---

## Qdrant


Vector database.


Stores:

- strategy embeddings
- game knowledge
- AI memory


Used by:

RAG system


---

# PostgreSQL Schema


## Users Table


Stores account information.


```sql
users

id UUID PRIMARY KEY

username VARCHAR

email VARCHAR

password_hash VARCHAR

created_at TIMESTAMP
```


Relationships:


```text
User

 |

 +

Player Profile

 |

 +

Matches
```


---

# Player Profiles Table


Stores long term player information.


```sql
player_profiles


id UUID PRIMARY KEY

user_id UUID FOREIGN KEY


game_username VARCHAR

current_rank VARCHAR

main_agent VARCHAR

playstyle VARCHAR


created_at TIMESTAMP
```


Example:


```json
{
    "rank":"Diamond",
    "playstyle":"Entry Fragger"
}
```


---

# Matches Table


Stores individual matches.


```sql
matches


id UUID PRIMARY KEY

player_id UUID FOREIGN KEY


map VARCHAR

agent VARCHAR

result VARCHAR


kills INT

deaths INT

assists INT


damage INT

created_at TIMESTAMP
```


---

# Match Statistics Table


Stores processed statistics.


```sql
match_statistics


id UUID PRIMARY KEY

match_id UUID FOREIGN KEY


headshot_percentage FLOAT

combat_score FLOAT

first_bloods INT

first_deaths INT

round_impact FLOAT
```


---

# ML Results Table


Stores machine learning outputs.


```sql
ml_results


id UUID PRIMARY KEY

player_id UUID FOREIGN KEY


aim_score FLOAT

consistency_score FLOAT

aggression_score FLOAT


predicted_role VARCHAR

detected_weakness VARCHAR


created_at TIMESTAMP
```


Example:


```json
{
    "aim_score":82,
    "aggression_score":91,
    "weakness":"over aggression"
}
```


---

# AI Reports Table


Stores generated coaching reports.


```sql
ai_reports


id UUID PRIMARY KEY

player_id UUID FOREIGN KEY


summary TEXT

recommendations JSON

created_at TIMESTAMP
```


Example:


```json
{
    "summary":
    "Strong mechanical player but inconsistent decisions",

    "recommendations":[
        "Reduce unnecessary fights",
        "Improve trading"
    ]
}
```


---

# AI Conversations


Stores chat history.


```sql
coach_messages


id UUID PRIMARY KEY


user_id UUID FOREIGN KEY


role VARCHAR

message TEXT


created_at TIMESTAMP
```


Roles:


```text
USER

AI
```


---

# Qdrant Collections


## Game Knowledge Collection


Stores FPS knowledge.


Vector:


```text
[0.132,0.532,0.763...]
```


Payload:


```json
{
    "topic":"map_strategy",
    "game":"valorant",
    "content":"..."
}
```


---

# Data Flow


Complete lifecycle:


```text
Player Match


     |

     v


PostgreSQL Storage


     |

     v


Feature Engineering


     |

     v


ML Processing


     |

     v


ML Results


     |

     v


AI Coach


     |

     v


Reports Database

```


---

# Future Scaling


Large scale improvements:


## Database


- read replicas
- partitioning
- indexing


---

## Analytics


Possible addition:


TimescaleDB


For:

- player trends
- historical performance


---

# Design Goals


Database design follows:


- normalized data
- scalable relations
- ML friendly structure
- easy analytics queries
