# 🏗️ ClutchAI Architecture

## System Overview

ClutchAI is an AI-powered FPS coaching platform.

The system converts raw competitive match data into meaningful insights using:

- Machine Learning
- Large Language Models
- Retrieval Augmented Generation
- Data Analytics

The goal is not to show statistics.

The goal is to explain performance.

---

# High Level Architecture

```text
                         Game APIs
                             |
                             v
                  Data Collection Layer
                             |
                             v
                  Feature Engineering
                             |
                             v

        ------------------------------------------------
        |                    |                         |
        v                    v                         v

   ML Engine            RAG System              Analytics Engine

        |                    |                         |

   Player Models       Game Knowledge        Performance Metrics

        ------------------------------------------------
                             |
                             v

                     AI Coach Engine

                             |
                             v

                    User Dashboard
```

---

# Components


## 1. Data Collection Service

Responsible for collecting and storing player data.


Responsibilities:

- Fetch player match history
- Store historical performance
- Normalize game statistics
- Prepare data for ML pipelines


Tech:

- FastAPI
- Async Python
- PostgreSQL
- Redis


---

## 2. Feature Engineering Pipeline


Transforms raw statistics into intelligent features.


Example Raw Data:

```text
kills = 20
deaths = 15
headshot_percentage = 24%
firstDeaths = 8
agent = Jett
map = Haven
```


Generated Features:

```text
aggression_score
entry_success_rate
consistency_score
impact_rating
aim_score
utility_score
```


Used by ML models for analysis.


Tech:

- Pandas
- NumPy
- Scikit Learn


---

# 3. Machine Learning Engine


The ML engine creates a deeper understanding of a player.


## Player Classification


Detects player archetypes:


Examples:

- Entry Fragger
- Support Player
- Lurker
- Passive Player
- Balanced Player


Algorithms:

- KMeans
- DBSCAN
- Embedding Similarity


---

## Weakness Detection


Predicts performance problems:


Examples:

- Poor aim consistency
- Bad agent selection
- Weak maps
- Over aggression
- Low impact rounds


Models:

- Random Forest
- XGBoost
- Neural Networks


---

# 4. AI Coach System


The AI coach combines:


```text
Player Profile

        +

ML Predictions

        +

Game Knowledge

        +

Historical Performance

        |

        v

Personalized Coaching
```


Example Output:


```text
Your defensive rounds are strong.

However your attacking rounds show a high first-death percentage.

You usually lose opening fights because your aggression score is high but trade percentage is low.

Recommended training:

- Improve timing
- Practice safer entries
- Play closer with teammates
```


Tech:

- LangChain
- LangGraph
- LLM APIs
- Structured Outputs


---

# 5. RAG Knowledge System


The AI coach uses external FPS knowledge.


Knowledge Sources:

- Agent guides
- Map strategies
- Patch notes
- Professional gameplay analysis
- Coaching resources


Pipeline:


```text
Documents

    |

Chunking

    |

Embedding Model

    |

Vector Database

    |

Retrieval

    |

LLM Reasoning

    |

AI Coach Response
```


Tech:

- Qdrant
- Sentence Transformers
- LangChain


---

# Database Layer


Stores:

- Users
- Matches
- Player statistics
- ML predictions
- AI conversations
- Generated reports


Database:

- PostgreSQL


Caching:

- Redis


---

# Future Architecture


## Gameplay Intelligence System


Future support for VOD analysis.


Pipeline:


```text
Gameplay Recording

        |

Frame Extraction

        |

Computer Vision

        |

Event Detection

        |

Vision Language Model

        |

AI Review
```


Features:

- Death analysis
- Aim mistakes
- Positioning feedback
- Utility usage review


Technologies:

- OpenCV
- YOLO
- Vision Language Models


---

# Design Philosophy


ClutchAI follows:

- Modular services
- ML-first architecture
- Scalable APIs
- Production ready engineering
- Easy model experimentation

The long term vision is to create a personal AI esports coach.
