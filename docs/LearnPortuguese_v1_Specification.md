# Learn Portuguese – Version 1 Specification

Repository: **nenolinkdk/nenoling-da-po**

Version: **1.0 (Draft)**

---

# Table of Contents

1. Purpose
2. Goals
3. Target Audience
4. Learning Philosophy
5. Application Overview
6. Lesson Structure
7. User Journey
8. Screen Specifications
9. Navigation
10. Functional Requirements
11. Data Model
12. JSON Structure
13. Progress Storage
14. Quiz Engine
15. Application Logic
16. Android Architecture
17. Testing
18. APK Build and Release
19. GitHub Workflow
20. Future Versions
21. Definition of Done

---

# 1. Purpose

Learn Portuguese is an offline Android application developed in Kotlin with Android Studio. It teaches Danish users European Portuguese (pt‑PT) through practical dialogues, repetition, pronunciation and quizzes.

The application requires no login, no Internet connection and stores all progress locally.

# 2. Goals

- 10 lessons
- 10 dialogues per lesson
- Danish → European Portuguese
- Grammar notes
- Vocabulary
- Text-to-Speech
- Local progress
- Offline operation
- APK for Android

# 3. Target Audience

- Danish beginners
- Tourists
- Students
- Business travellers
- Expats

Only European Portuguese is used.

# 4. Learning Philosophy

Users learn through realistic situations.

Each lesson contains:
- introduction
- dialogues
- vocabulary
- grammar
- quiz

Recommended lesson duration: 15–20 minutes.

# 5. Application Overview

Home

↓

Lesson

↓

Dialogue

↓

Quiz

↓

Result

↓

Next lesson

# 6. Lesson Structure

Each lesson contains:

- Lesson introduction
- 10 dialogues
- 10–20 phrases per dialogue
- Vocabulary
- Grammar
- Quiz

Suggested lessons:

1. Greetings
2. Introducing yourself
3. Numbers, dates and time
4. Family
5. Food
6. Restaurant
7. Transport
8. Hotel
9. Shopping
10. Everyday conversations

# 7. User Journey

First launch:

- Welcome screen
- Start Learning

Home Screen:

- Progress bar
- Continue Learning
- Lesson list

Dialogue Screen:

- Portuguese
- Danish translation
- Grammar
- Vocabulary
- Pronounce
- Previous / Next

Quiz:

5 multiple-choice questions.

Completion:

- Lesson marked complete
- Progress updated
- Star awarded

# 8. Screen Specifications

Screens:

- Splash
- Home
- Lesson
- Dialogue
- Vocabulary
- Grammar
- Quiz
- Result
- Progress
- Settings

Material Design 3 shall be used.

# 9. Navigation

Primary flow:

Home → Lesson → Dialogue → Quiz → Result

Secondary:

Vocabulary

Grammar

Settings

Progress

Search

# 10. Functional Requirements

The application shall support:

- Offline lessons
- Local JSON data
- Progress tracking
- Favourites
- Search
- Text-to-Speech
- Quiz
- Continue where the learner stopped

# 11. Data Model

Recommended structure:

```
assets/
    lessons/
        lesson01.json
        ...
        lesson10.json
```

Lesson:

- id
- title
- description
- dialogues

Dialogue:

- title
- phrases
- vocabulary
- grammar

Phrase:

- Portuguese
- Danish
- audio (optional)

# 12. JSON Structure

Example:

```json
{
  "id":1,
  "title":"Greetings",
  "dialogues":[
    {
      "id":1,
      "title":"Morning",
      "phrases":[
        {
          "portuguese":"Bom dia.",
          "danish":"Godmorgen."
        }
      ]
    }
  ]
}
```

# 13. Progress Storage

Use Android DataStore.

Store:

- last lesson
- last dialogue
- completed lessons
- quiz scores
- favourites
- settings

# 14. Quiz Engine

Five questions.

Question types:

- Danish → Portuguese
- Portuguese → Danish
- Vocabulary

Scoring:

0–2 Repeat

3–4 Passed

5 Excellent

# 15. Application Logic

```
Home
 ↓
Lesson
 ↓
Dialogue
 ↓
Quiz
 ↓
Result
 ↓
Save progress
```

# 16. Android Architecture

Language:

- Kotlin

IDE:

- Android Studio

Architecture:

- MVVM

Libraries:

- AndroidX
- Material Design 3
- Navigation Component
- DataStore
- RecyclerView

Text-to-Speech locale:

```
Locale("pt","PT")
```

# 17. Testing

Verify:

- Navigation
- Lessons
- Dialogues
- Vocabulary
- Grammar
- Quiz
- Progress
- Text-to-Speech

Test on:

- Emulator
- Android phone
- Android tablet

# 18. APK Build and Release

Development:

Debug APK

Release:

Signed APK

Versioning:

0.1 Planning

0.5 Lessons

0.8 Quiz

0.9 Beta

1.0 Release

# 19. GitHub Workflow

Repository:

```
nenolinkdk/nenoling-da-po
```

Suggested branches:

- main
- develop
- feature/navigation
- feature/lessons
- feature/quiz
- feature/audio

Workflow:

Feature → Commit → Push → Review → Merge → Test → Release

# 20. Future Versions

Version 2

- Google Play
- Statistics
- More lessons

Version 3

- Cloud sync
- Web version
- Multiple languages

Version 4

- AI conversation partner
- Speech recognition

# 21. Definition of Done

A feature is complete when:

- Code compiles
- Navigation works
- No crashes
- Progress saved
- Documentation updated
- Tested on physical Android device

---

End of Specification
