# 🧩 ClutchAI System Design


## Overview


ClutchAI follows a modular AI system architecture.


The system is separated into independent layers:


```text
Frontend

    |

API Gateway

    |

Backend Services

    |

Processing Layer

    |

AI / ML Systems

    |

Database Layer
```


This separation allows:

- independent scaling
- easier debugging
- faster ML experimentation


---

# Complete System Flow


```text

                 User

                  |

                  v


          Next.js Frontend


                  |

                  v


            FastAPI Server


                  |

        ----------------------

        |                    |

 Match Service        AI Coach Service


        |                    |

        v                    v


Feature Pipeline       RAG Pipeline


        |                    |

        v                    v


 ML Models          Vector Database


        |                    |

        -----------+---------


                    |

                    v


              Final Insights


                    |

                    v


              User Dashboard

```


---

# Backend Architecture


The backend follows service based architecture.


Structure:


```text
backend/

├── app/

│

├── api/

│   └── routes

│

├── services/

│   ├── match_service

│   ├── user_service

│   ├── ai_service

│   └── ml_service

│

├── models/

│

├── schemas/

│

├── database/

│

└── workers/

```


---

# Data Processing Flow


## Step 1: Match Collection


External game APIs provide match information.


Collected:

- player stats
- match history
- agents
- maps
- weapons


Stored inside PostgreSQL.


---

# Step 2: Feature Engineering


Raw data is transformed.


Example:


Before:


```text
Kills

Deaths

Damage

Accuracy
```


After:


```text
Impact Rating

Aim Score

Consistency Score

Aggression Score

Role Score
```


---

# Step 3: Machine Learning Layer


ML systems consume engineered features.


Tasks:


## Classification

Find player weaknesses.


## Clustering

Find similar players.


## Prediction

Estimate improvement areas.


---

# Step 4: AI Reasoning Layer


The AI coach receives:


```text
Player Statistics

+

ML Analysis

+

Retrieved Game Knowledge

=

Personalized Coaching

```


---

# Async Processing


Heavy tasks are processed asynchronously.


Examples:

- Fetching match history
- Running ML models
- Creating AI reports


Architecture:


```text
FastAPI

   |

Redis Queue

   |

Celery Worker

   |

Processing Job

```


---

# Database Design Philosophy


PostgreSQL stores structured data.


Examples:

- users
- matches
- statistics
- reports



Qdrant stores unstructured knowledge.


Examples:

- strategies
- guides
- patches


---

# Scaling Strategy


## Small Scale


Single server:

- API
- Database
- Worker


---

## Production Scale


Separate:


- Backend servers

- Worker machines

- Database server

- Vector database

- Model servers


---

# Future Vision System


Video analysis service:


```text
Gameplay Video

      |

Frame Extractor

      |

Vision Model

      |

Event Detection

      |

AI Coach

```


This will be independent from the statistics system.
