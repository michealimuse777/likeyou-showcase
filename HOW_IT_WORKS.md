# System Overview: AI & Matching Architecture

This document provides a high-level technical overview of the AI systems driving **LikeYou**, focusing on the semantic matching architecture.

## Core Concept: Semantic Matching

Traditional platforms rely on explicit filters (age, location) or tag-based matching. **LikeYou** employs **Semantic Matching** to interpret the underlying context and meaning of user profiles.

### 1. Vector Embedding Generation
When a user profile is created or updated:
1.  **Input Analysis**: The system aggregates the user's bio, interests, and responses to personality assessment questions.
2.  **Embedding Model**: This aggregated text is processed through **Google Gemini's Embedding Model**.
3.  **Vectorization**: The model yields a high-dimensional vector representation of the user's semantic profile.

### 2. Similarity Search with `pgvector`
Matches are identified through mathematical proximity rather than keyword overlap:
-   Vectors are stored in a **PostgreSQL** database utilizing the `pgvector` extension.
-   The system performs a **Cosine Similarity** search to rank potential matches.
-   This approach identifies users with semantically similar values and articulation styles, regardless of specific vocabulary differences.

### 3. AI-Driven Conversation Initiation
Upon establishing a match:
1.  **Context Loading**: The system retrieves the profile context for both users.
2.  **Generative Prompting**: A structured prompt is sent to **Google Gemini**.
3.  **Output**: The AI generates a personalized, context-aware conversation starter designed to bridge shared interests or complementary traits.

## Architecture Diagram

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

## Security & Privacy
-   **Server-Side Logic**: Proprietary prompts and model tuning parameters are executed server-side and are never exposed to the client.
-   **Data Security**: User data access is strictly controlled via Row Level Security (RLS) policies within Supabase.
