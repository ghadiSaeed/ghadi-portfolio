# Anah - Portfolio Case Study Draft

> Status: Evidence-backed working draft. The project facts are supported by the final report and repository. The personal-contribution section must be confirmed by Ghadi before this content is finalized or added to the portfolio.

## Project overview

Anah is an Arabic-first, AI-powered web application designed to help users reflect on and better understand their emotional well-being. The platform combines guided journaling, mood tracking, Arabic emotion analysis, personalized recommendations, visual mood insights, daily task support, and an AI-powered conversational assistant in one culturally adapted experience.

The final system uses a hybrid AI architecture: a MARBERTv2-based classifier analyzes Arabic journal entries, while an OpenAI-powered chatbot generates context-aware supportive responses. A Flask backend connects the user interface with the AI services, Firebase, externally hosted model weights, and the deployed Render application.

- **Project type:** University graduation project, Computer Science Department, University of Jeddah
- **Year:** 2026
- **Team size:** Five students
- **Repository:** [github.com/galaadnan/anahWeb](https://github.com/galaadnan/anahWeb)
- **Deployment documented in the report:** [anahweb.onrender.com](https://anahweb.onrender.com)

## Problem statement

The project responds to a gap identified through the team's research: Arabic-speaking users have limited access to digital mental-health tools that combine cultural relevance with intelligent emotional analysis and personalized self-reflection features. Existing options often emphasize therapist communication or general wellness content, while offering limited Arabic emotion detection, mood tracking, personalization, or interactive support.

Anah was designed as a unified Arabic experience where users can journal or select a mood, receive emotional insights, follow changes over time, and access supportive recommendations and conversation. It is a self-reflection and emotional-support tool, not a replacement for professional mental-health care.

## Key features

- **Arabic journaling:** A structured writing space with prompts, text styling, image support, streaks, and achievements.
- **Emotion analysis:** Sentence-level processing of Arabic journal entries using a MARBERTv2-based model.
- **Primary and secondary emotion detection:** Mixed emotional signals are summarized using emotion frequency and confidence scores.
- **Mood selection:** Users can record their state through an emoji-based alternative to journal input.
- **Mood-analysis dashboard:** Charts, emotion distributions, recent history, and time filters help users review emotional patterns.
- **Personalized recommendations:** A knowledge-based recommendation system maps detected emotions to relevant well-being suggestions.
- **Emotion-aware quotes:** Motivational quotes are selected based on the user's detected or recorded mood.
- **AI-powered chatbot:** A `gpt-4o-mini` assistant provides Arabic, context-aware, supportive responses informed by emotional context.
- **Message to Yourself:** Users can write a reflective message and schedule it to reappear later.
- **Daily task checklist:** Users can select a task icon, enter a task, choose its duration, and track daily progress.
- **Accounts and cloud data:** Firebase Authentication supports registration, login, verification, and password reset; Firestore stores user-related records.
- **Privacy-oriented session behavior:** The documented system automatically logs users out after five minutes of inactivity.

## Technologies used

### Frontend

- HTML5
- CSS3 and responsive/mobile styling
- JavaScript
- Chart.js for emotion visualizations

### Backend and AI

- Python and Flask
- PyTorch
- Hugging Face Transformers
- MARBERTv2-based Arabic emotion classifier
- Sentence segmentation and confidence/frequency-based emotion aggregation
- OpenAI API with `gpt-4o-mini`

### Cloud, data, and deployment

- Firebase Authentication
- Cloud Firestore
- Render
- Google Drive for the large `model.safetensors` file
- Google Colab for model training
- Git and GitHub

## My role and contributions - pending confirmation

The Git history contains **28 commits attributed to `ghadiSaeed <ghadi6249@gmail.com>`**. Based strictly on those commits, the following contribution statement is supportable if you confirm that this GitHub identity and work are yours:

> I contributed across frontend development, responsive UX, and AI feature integration. I integrated and iterated the OpenAI-powered chatbot, improving its emotional context, lightweight memory, response constraints, cross-page access, and typing feedback. I implemented the “Message to Yourself” experience, contributed the mood-aware Arabic quote system, improved task-duration controls, and resolved synchronization issues between journal analysis and emoji mood input. I also redesigned key mobile layouts across navigation, the home experience, journaling, analysis, and the chatbot.

Repository-supported contribution details:

- Added an OpenAI chat endpoint and replaced a machine-specific model path with a relative project path (`14caac8`).
- Enhanced chatbot context, lightweight emotional memory, prompt behavior, and response-length/cost controls (`f75b194`, `816cadf`, `fb82587`).
- Added chatbot access across the journal and analysis pages (`c74cc9f`).
- Implemented the “Message to Yourself” interface, scheduling logic, and confirmation flow (`667e219`).
- Developed and refined mood-based motivational quote logic and added the Arabic quote dataset (`773d82e`, `4c80a30`).
- Improved the task-duration picker and custom-duration workflow (`d5a7cca`).
- Fixed journal-versus-emoji input priority and synchronized mood results across the home, journal, and analysis experiences (`db0916f`, `15e8fd3`, `618ecea`, `5a5f92d`, `282c019`).
- Improved responsive navigation and analysis layouts, then consolidated the mobile redesign in `mobile.css` (`db3e774`, `14b2346`, `fb82587`, `c9c621c`).

The report and team page use the name **Ghadi Alghamdi**, while the portfolio uses **Ghadi Saeed**. This identity must be confirmed before the section is published. The repository does not clearly establish whether Ghadi also participated in model training, Firebase setup, testing, research, or report writing.

## Challenges and solutions

### 1. Limited Arabic emotion detection

**Challenge:** The initial system relied on rule-based analysis and emoji selection, which could not reliably represent Arabic dialects or mixed emotional states.

**Solution:** The team integrated a MARBERTv2-based classifier, added sentence-level analysis, and combined frequency with confidence scores to identify primary and secondary emotions. Explicit Arabic emotion rules remain as a complementary layer in the current backend.

### 2. Repetitive chatbot responses

**Challenge:** The original rule-based chatbot produced predefined, repetitive responses and struggled with unexpected input.

**Solution:** The chatbot was upgraded to `gpt-4o-mini` through the Flask backend. The implementation adds emotional context to the prompt and includes lightweight memory and response constraints to keep interactions more relevant and efficient.

### 3. Unstructured local data

**Challenge:** Early browser-based storage made user records difficult to organize and limited account support and scalability.