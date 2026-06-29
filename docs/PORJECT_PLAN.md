# Learn Portuguese

## Project Plan

**Repository**

`nenolinkdk/nenoling-da-po`

---

# 1. Project Vision

Develop a professional Android application that enables Danish-speaking beginners to learn European Portuguese through practical conversations, repetition and quizzes.

The application must work completely offline and provide an intuitive user experience suitable for self-study.

---

# 2. Project Objectives

Version 1 shall include:

* Android application
* Offline operation
* APK installation
* 10 structured lessons
* 10 dialogues in every lesson
* Pronunciation support
* Local progress tracking
* Lesson quizzes

The application should be easy to expand in future versions.

---

# 3. Success Criteria

The project is successful when a user can:

* Install the APK.
* Complete all ten lessons.
* Listen to Portuguese pronunciation.
* Complete quizzes.
* Resume learning after closing the app.
* Use the application without Internet access.

---

# 4. Target Users

Primary users:

* Danish beginners
* Tourists
* Students
* Business travellers
* People relocating to Portugal

Language variant:

**European Portuguese (pt-PT)**

---

# 5. Scope – Version 1

Included:

* Offline application
* Android only
* Material Design 3
* Local JSON lesson data
* DataStore progress
* Text-to-Speech
* Quiz system
* Lesson completion
* Progress overview

Not included:

* Login
* Cloud storage
* Online database
* User accounts
* Advertisements
* Google Play billing

---

# 6. Functional Requirements

The application shall provide:

### Lessons

10 lessons.

Each lesson contains:

* lesson introduction
* 10 dialogues
* vocabulary
* grammar notes
* pronunciation
* quiz

---

### Navigation

Home Screen

↓

Lesson List

↓

Dialogue

↓

Quiz

↓

Result

↓

Next Lesson

---

### Progress

Store locally:

* completed lessons
* completed dialogues
* quiz score
* last position

---

### Pronunciation

Android Text-to-Speech

Preferred language:

Portuguese (Portugal)

Fallback:

Display a message if Portuguese voice is unavailable.

---

# 7. Technical Requirements

Language:

Kotlin

IDE:

Android Studio

Minimum SDK:

Android 10

Target SDK:

Latest stable Android version

Architecture:

MVVM

Material Design 3

Storage:

DataStore

Lesson content:

JSON files

---

# 8. User Interface

Simple

Large buttons

Readable typography

Dark Mode support

Responsive layouts

Accessible colours

---

# 9. Development Phases

## Phase 1

Project documentation

Repository structure

Architecture

---

## Phase 2

Navigation

Home screen

Lesson structure

---

## Phase 3

Lesson content

Dialogues

Vocabulary

Grammar

---

## Phase 4

Quiz system

Progress tracking

Achievements

---

## Phase 5

Testing

Bug fixing

Performance

---

## Phase 6

APK generation

Documentation

Release

---

# 10. Milestones

Milestone 1

Documentation complete

Milestone 2

Application framework complete

Milestone 3

Lessons implemented

Milestone 4

Quiz implemented

Milestone 5

Text-to-Speech implemented

Milestone 6

APK successfully installed

Milestone 7

Version 1.0 released

---

# 11. Risks

Possible risks:

* Android Text-to-Speech not available
* Large lesson content
* Navigation complexity
* Different Android versions

Mitigation:

* Modular architecture
* Local data only
* Incremental testing
* GitHub version control

---

# 12. Future Versions

Version 2

* Google Play release
* More lessons
* More quizzes
* Statistics

Version 3

* Cloud synchronisation
* Multiple user profiles
* Vocabulary trainer

Version 4

* Web application
* Shared database
* AI conversation partner

---

# 13. Repository Structure

```
docs/
README.md
PROJECT_PLAN.md
LearnPortuguese_v1_Specification.md
LessonPlan.md
UI_Design.md
DataModel.md
QuizSystem.md
AndroidStudio_Workflow.md
GitHub_Workflow.md
Future_Versions.md
CHANGELOG.md

app/

assets/

images/

apk/
```

---

# Current Status

Status:

Planning

Version:

0.1

Next Document:

**LearnPortuguese_v1_Specification.md**
