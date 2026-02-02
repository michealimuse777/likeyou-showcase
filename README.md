# LikeYou V3

**A premium AI-powered social connector built for meaningful connections.**

> [!NOTE]
> This is a public showcase repository. The source code, AI models, and backend logic are private.

## Live Demonstration

**[Visit the live application](https://likeyou-lac.vercel.app/)**

---

## About the Project

LikeYou V3 is a next-generation social discovery platform designed to solve the problem of superficial online interactions. By leveraging large language models (LLMs) and vector search technology, the application analyzes user personalities to foster genuine connections.

The goal was to move beyond simple "swiping" and create an environment where matches are driven by semantic compatibility—connecting people based on what they value, how they think, and who they truly are.

## Interface Overview

| Landing Page | Chat Interface |
|:---:|:---:|
| ![Landing Page](assets/landing.png) | ![Chat Interface](assets/chat.png) |

| AI Matching | Profile View |
|:---:|:---:|
| ![AI Matching](assets/connections.png) | ![Profile View](assets/profile.png) |

---

## Key Features

-   **Semantic AI Matching**: Matches are curated based on vector embeddings of user interests, values, and bios using Google Gemini AI.
-   **Real-Time Messaging**: Robust, low-latency chat infrastructure powered by Stream Chat.
-   **Premium UI**: A high-fidelity, immersive aesthetic designed with Tailwind CSS, Framer Motion, and Shadcn/UI.
-   **Comprehensive Profiles**: Detailed profile system featuring avatar uploads and psychological profiling.

## Key Packages & Libraries

This project utilizes a robust suite of modern libraries to deliver a high-performance experience:

### Core Framework
-   **next**: The React framework for the web.
-   **react / react-dom**: UI library for building interactive interfaces.

### AI & Data
-   **@google/generative-ai**: Integration with Google's Gemini Pro models.
-   **@supabase/supabase-js**: Client for Supabase database, auth, and storage.
-   **pgvector**: PostgreSQL extension for vector similarity search.

### UI & Animation
-   **framer-motion**: Production-ready animation library for React.
-   **tailwindcss**: Utility-first CSS framework.
-   **lucide-react**: Beautiful, consistent icon set.
-   **sonner**: An opinionated toast component for React.

### Real-time Communication
-   **stream-chat**: JS SDK for Stream Chat.
-   **stream-chat-react**: React components for Stream Chat.

---

## System Architecture

For a technical overview of the AI matching logic, please refer to the [System Overview](./HOW_IT_WORKS.md).

---

*Created by Imuse Michael*
