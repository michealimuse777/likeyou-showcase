# 🧠 How LikeYou Works

This document provides a high-level overview of the AI systems driving **LikeYou**, without exposing specific codebase logic.

## The Core Concept: Semantic Matching

Traditional apps match users based on simple filters (age, location) or shallow tags. **LikeYou** uses **Semantic Matching** to understand the *meaning* behind what users say about themselves.

### 1. The "Soul" Vector
When a user accounts is created or updated:
1.  **Input Analysis**: The user's bio, interests, and answers to deep questions are collected.
2.  **Embedding Generation**: We pipe this text through **Google Gemini's Embedding Model**.
3.  **Vectorization**: The AI converts the text into a high-dimensional vector (a list of numbers) representing the "semantic soul" of the user.

### 2. Finding Matches with `pgvector`
Instead of looking for exact text matches, we look for **mathematical closeness**:
-   We store these vectors in a **PostgreSQL** database using the `pgvector` extension.
-   When searching for matches, we perform a **Cosine Similarity** search.
-   This finds users whose vectors point in a similar "direction" in the high-dimensional space—meaning they think, write, and value similar things, even if they use different words.

### 3. The "Icebreaker" AI
Once a match is found:
1.  **Context Loading**: The system retrieves the profiles of both users.
2.  **Generative Prompting**: A specialized prompt is sent to **Google Gemini**.
3.  **Output**: The AI generates a unique, personalized conversation starter based on shared interests or complementary traits found in their profiles.

## Architecture Overview

```mermaid
graph TD
    User[User Client] -->| Bio & Traits | API[Next.js API Layer]
    API -->| Raw Text | Gemini[Google Gemini AI]
    Gemini -->| Vector Embeddings | API
    API -->| Store Vector | DB[(Supabase + pgvector)]
    
    User -->| "Find Matches" | API
    API -->| Query Nearest Neighbors | DB
    DB -->| Semantic Matches | API
    API -->| Top Profiles | User
```

## Privacy & Security
-   **Private Logic**: The specific prompts and tuning parameters for the AI models remain server-side and are never exposed to the client.
-   **Data Safety**: User data is secured using Row Level Security (RLS) policies in Supabase.
