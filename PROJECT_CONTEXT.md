# 🧠 ClutchAI Project Context


## What is ClutchAI?


ClutchAI is an AI-powered esports coaching platform.


The mission:

Turn player data into personalized coaching.


Most gaming trackers only answer:


```text
"What happened?"
```


Example:


```text
Kills: 15
Deaths: 18
Win Rate: 48%
```


ClutchAI answers:


```text
"Why did it happen?"

and

"How do I improve?"
```


Example:


```text
Your mechanical skill is improving.

However your win rate is low because:

- your first death percentage is high
- your aggression is above average
- your trade success is low

Focus on safer entries and timing.
```


---

# Core Philosophy


ClutchAI is NOT a stats website.


It is:

```text
Performance Data

        +

Machine Learning

        +

Game Knowledge

        +

LLM Reasoning


        =


Personal AI Coach
```


---

# Product Inspiration


Inspired by:

- esports coaches
- FPS analytics platforms
- AI assistants


Goal:

Create a personal coach available anytime.


---

# Current MVP Goal


Build:


```text
AI FPS Performance Analyst
```


NOT:


```text
Real time gameplay analyzer
```


Gameplay video analysis is a future expansion.


Current focus:


- collect statistics
- analyze patterns
- detect weaknesses
- generate coaching


---

# MVP Features


## Player Dashboard


Shows:


- matches
- performance trends
- strengths
- weaknesses
- improvement areas



---

# Match Intelligence


Input:


```text
Raw Match Statistics
```


Examples:


```text
Kills

Deaths

Assists

Damage

Accuracy

Agents

Maps

Rounds

Win/Loss
```


Converted into:


```text
Performance Profile
```


Example:


```json
{
    "aim":82,
    "consistency":64,
    "aggression":90,
    "impact":75
}
```


---

# Machine Learning Goals


ML should answer:


## What type of player is this?


Examples:


```text
Entry Fragger

Support

Lurker

Balanced
```


---


## What is holding the player back?


Examples:


```text
Aim

Decision making

Consistency

Agent choice

Aggression

Map weakness
```


---

# ML Models Planned


## Clustering


Purpose:

Group similar players.


Algorithms:


- KMeans
- DBSCAN



---


## Classification


Purpose:

Predict weaknesses.


Algorithms:


- Random Forest
- XGBoost


---

# AI Coach Goal


The AI coach receives:


```text
User Question

+

Player Profile

+

ML Insights

+

Game Knowledge

```


Returns:


```text
Personalized Advice
```


Example:


User:


```text
Why am I stuck Gold?
```


AI:


```text
Your mechanics are above average for Gold.

Your biggest weakness is consistency.

Your last 20 matches show large performance swings.

Recommended plan:

1. Reduce unnecessary duels
2. Improve defensive positioning
3. Play fewer agents
```


---

# RAG Purpose


LLMs should not guess game knowledge.


Use RAG for:


- strategies
- agents
- maps
- patches
- meta changes


Pipeline:


```text
Knowledge Sources

        |

Chunking

        |

Embeddings

        |

Qdrant

        |

Retrieval

        |

AI Coach

```


---

# Backend Principles


Use production practices.


Rules:


- Async FastAPI
- Clean services
- Separation of concerns
- Typed schemas
- Dependency injection
- Background workers


Avoid:


- Business logic inside routes
- Hardcoded prompts
- Large files
- Mixed ML/API logic


---

# Backend Structure Goal


```text
backend/


app/


api/

services/

models/

schemas/

database/

workers/

core/

ml/

ai/

```


---

# Frontend Goal


Create a modern SaaS dashboard.


Pages:


```text
/


Landing Page


/dashboard


Analytics


/coach


AI Chat


/profile


Player Details

```


---

# AI Engineering Rules


Do not simply call an LLM.


Bad:


```text
Stats → Prompt → Response
```


Good:


```text
Stats

↓

Feature Engineering

↓

ML Analysis

↓

Retrieve Knowledge

↓

LLM Reasoning

↓

Structured Response

```


---

# Future Expansion


## Gameplay Analysis


Later add:


```text
Gameplay Video

        |

Frame Extraction

        |

Computer Vision

        |

Vision Model

        |

AI Review
```


Possible technologies:


- OpenCV
- YOLO
- Vision Language Models


---

# Long Term Vision


ClutchAI should become:


```text
The AI performance coach for competitive gamers.
```


A platform that understands:

- how you play
- why you lose
- how you improve


---

# Developer Reminder


Build like a production AI product.


Not a demo.

Not a wrapper.


Every feature should answer:


"Does this help the player improve?"
