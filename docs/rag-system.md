# 📚 ClutchAI RAG System


## Overview


The Retrieval Augmented Generation system gives the AI coach game knowledge.


LLMs alone do not understand:

- current meta
- agent strategies
- map tactics
- patches


RAG solves this by giving the model external knowledge.


---

# Why RAG?


Without RAG:


```text
User Question

      |

      v

LLM

      |

Generic Advice
```


Problem:

- outdated knowledge
- hallucinations
- no game-specific reasoning


---

With RAG:


```text
User Question

        |

        v

Retrieve Relevant Knowledge

        |

        v

LLM + Context

        |

        v

Personalized Coaching
```


---

# Knowledge Sources


The knowledge database contains:


## Game Knowledge

Examples:

- Agents
- Maps
- Abilities
- Weapons
- Economy


---


## Strategy Knowledge


Examples:

- attacking strategies
- defensive setups
- positioning rules
- team play


---


## Meta Knowledge


Examples:

- patch changes
- agent buffs
- nerfs
- professional trends


---

# Ingestion Pipeline


```text
Documents

    |

Cleaning

    |

Chunking

    |

Embedding Generation

    |

Vector Storage

    |

Retrieval
```


---

# Chunking Strategy


Documents are split into meaningful sections.


Example:


Original:

```text
Complete Haven Map Guide
```


Chunks:

```text
Haven A Site Strategy

Haven B Site Strategy

Haven C Retake Strategy
```


---

# Embeddings


Text is converted into vectors.


Models:


- BGE
- E5
- OpenAI Embeddings


Example:


```text
"How to attack Haven A?"

              |

              v

Vector Search

              |

              v

Retrieve Haven strategies
```


---

# Vector Database


Database:

Qdrant


Stores:

- embedding vector
- text chunk
- metadata


Metadata:


```json
{
    "game": "valorant",
    "map": "haven",
    "topic": "attack"
}
```


---

# AI Coach Pipeline


Complete flow:


```text
User Question

+

Player Statistics

        |

        v

Retrieve Game Knowledge

        |

        v

Combine Context

        |

        v

LLM Reasoning

        |

        v

Coach Response
```


---

# Future Improvements


Advanced RAG:


- hybrid search
- reranking
- query rewriting
- agent workflows


Framework:

LangGraph

