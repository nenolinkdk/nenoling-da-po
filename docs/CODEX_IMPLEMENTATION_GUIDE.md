# CODEX IMPLEMENTATION GUIDE

Project: **Learn Portuguese**  
Repository: **nenolinkdk/nenoling-da-po**  
Target file location: `docs/CODEX_IMPLEMENTATION_GUIDE.md`

---

# 1. Purpose

This document is the practical implementation guide for Codex.

Codex shall use this guide together with:

`docs/LearnPortuguese_v1_Specification.md`

The goal is to build Version 1 of the Android app **Learn Portuguese**.

The app teaches Danish users European Portuguese and works offline.

---

# 2. General Instructions for Codex

Codex must:

- keep the project simple
- use Kotlin
- use Android Studio project conventions
- use Material Design 3 where possible
- use local JSON data
- use DataStore or SharedPreferences for progress
- support offline use
- support Android Text-to-Speech with Portuguese Portugal
- avoid unnecessary external dependencies
- commit changes in small logical steps
- update documentation when behaviour changes

Codex must not:

- add login
- add cloud database
- add advertising
- add payment features
- use Brazilian Portuguese as default
- remove existing working functionality without explicit instruction

---

# 3. Recommended Implementation Phases

## Phase 1 – Repository and project cleanup

Tasks:

1. Inspect the existing Android project.
2. Confirm Gradle builds.
3. Confirm package name and app name.
4. Remove unused demo code if necessary.
5. Keep existing working screens unless replacement is required.
6. Add or update documentation folder.

Expected result:

- Project opens in Android Studio.
- Gradle sync works.
- App can run on emulator or phone.

---

## Phase 2 – Basic app structure

Create or verify the following structure:

```text
app/src/main/
    java/ or kotlin/
        data/
        data/model/
        data/repository/
        data/datastore/
        ui/
        ui/home/
        ui/lesson/
        ui/dialogue/
        ui/quiz/
        ui/progress/
        ui/settings/
        tts/
        utils/
    assets/
        lessons/
```

Expected result:

- Clean structure for future development.
- No lesson content hardcoded directly into UI screens if avoidable.

---

## Phase 3 – Data model

Create Kotlin data classes for:

- Lesson
- Dialogue
- Phrase
- VocabularyItem
- GrammarNote
- QuizQuestion
- QuizAnswer
- UserProgress

Suggested model:

```kotlin
data class Lesson(
    val id: Int,
    val title: String,
    val description: String,
    val dialogues: List<Dialogue>,
    val quiz: List<QuizQuestion>
)

data class Dialogue(
    val id: Int,
    val title: String,
    val objective: String,
    val phrases: List<Phrase>,
    val vocabulary: List<VocabularyItem>,
    val grammar: List<GrammarNote>
)

data class Phrase(
    val portuguese: String,
    val danish: String
)
```

Expected result:

- App has a clear data model for all lesson content.

---

## Phase 4 – JSON lesson data

Create local JSON files:

```text
app/src/main/assets/lessons/
    lesson01.json
    lesson02.json
    lesson03.json
    lesson04.json
    lesson05.json
    lesson06.json
    lesson07.json
    lesson08.json
    lesson09.json
    lesson10.json
```

Each lesson must contain:

- lesson id
- lesson title
- description
- 10 dialogues
- vocabulary
- grammar note
- quiz questions

Start with complete sample data for Lesson 1.

For the remaining lessons, create structured placeholder data if full content is not yet ready.

Expected result:

- App can load lesson data locally.

---

## Phase 5 – Lesson repository

Create a repository class such as:

```kotlin
class LessonRepository
```

Responsibilities:

- load JSON files from assets
- parse lessons
- return all lessons
- return one lesson by ID
- handle loading errors gracefully

Expected result:

- UI does not load JSON directly.
- All lesson access goes through repository.

---

## Phase 6 – Home screen

Build the Home Screen.

Required elements:

- title: Learn Portuguese
- progress bar
- Continue Learning button
- list of 10 lessons
- completed lesson indicators
- settings button if possible

Behaviour:

- tapping a lesson opens that lesson
- Continue Learning opens the last unfinished dialogue
- completed lessons show a star or checkmark

Expected result:

- User can start or continue learning from the Home Screen.

---

## Phase 7 – Lesson overview screen

Build a Lesson Screen.

Required elements:

- lesson title
- lesson description
- number of dialogues
- dialogue list
- quiz button
- back button

Behaviour:

- selecting a dialogue opens the Dialogue Screen
- quiz is available after dialogue completion, or always available in Version 1 if simpler

Expected result:

- User can browse all 10 dialogues in a lesson.

---

## Phase 8 – Dialogue screen

Build the Dialogue Screen.

Required elements:

- lesson title
- dialogue title
- dialogue number, e.g. "Dialogue 3 of 10"
- Portuguese phrases
- Danish translations
- vocabulary
- grammar note
- Previous button
- Next button
- Pronounce button
- Favourite button if simple to implement

Behaviour:

- Next moves to next dialogue
- Previous moves to previous dialogue
- after dialogue 10, user is offered the quiz
- progress is saved automatically

Expected result:

- User can work through all dialogues in order.

---

## Phase 9 – Text-to-Speech

Implement Android Text-to-Speech.

Preferred locale:

```kotlin
Locale("pt", "PT")
```

Behaviour:

- pronounce only Portuguese text
- if pt-PT is unavailable, show a clear message
- allow repeated playback
- avoid crashing if TTS is not installed

Suggested message:

```text
Portuguese voice is not available on this device.
```

Expected result:

- User can hear Portuguese pronunciation where supported.

---

## Phase 10 – Progress storage

Implement local progress storage.

Use:

- DataStore Preferences, or
- SharedPreferences if simpler

Store:

- last lesson ID
- last dialogue ID
- completed lessons
- quiz scores
- favourite phrases if implemented

Expected result:

- Closing and reopening the app preserves user progress.

---

## Phase 11 – Quiz engine

Each lesson has a simple quiz.

Requirements:

- 5 questions
- multiple choice
- Danish → Portuguese focus
- one correct answer
- three wrong answers
- score shown at the end

Scoring:

```text
0–2: Repeat lesson
3–4: Passed
5: Excellent
```

Expected result:

- User can complete a short quiz after each lesson.

---

## Phase 12 – Result screen

Build a Result Screen.

Required elements:

- score
- pass/fail message
- correct answers
- repeat lesson button
- next lesson button
- home button

Behaviour:

- if score is 3 or more, mark lesson as completed
- update progress
- show star or checkmark

Expected result:

- User receives clear feedback after quiz completion.

---

## Phase 13 – Progress screen

Build a simple Progress Screen.

Required elements:

- total lessons completed
- progress bar
- quiz scores
- last active lesson
- completed lesson list

Expected result:

- User can see how far they have progressed.

---

## Phase 14 – Settings screen

Build a simple Settings Screen.

Settings:

- enable/disable pronunciation
- speech speed if simple
- reset progress
- app information

Important:

Reset progress must ask for confirmation.

Expected result:

- User can control basic app behaviour.

---

## Phase 15 – UI improvement

Apply consistent UI.

Use:

- Material Design 3
- readable typography
- large buttons
- clear spacing
- portrait-first design
- light and dark mode where possible

Expected result:

- App looks clean and usable on a phone.

---

## Phase 16 – Error handling

Handle:

- missing JSON files
- invalid JSON
- unavailable TTS
- empty lesson data
- navigation errors

Do not crash.

Show clear user messages.

Expected result:

- App remains stable even if data is incomplete.

---

## Phase 17 – Testing

Test the following:

- app starts
- lesson list loads
- all 10 lessons appear
- dialogue navigation works
- quiz works
- progress is saved
- TTS does not crash
- APK installs on phone

Expected result:

- Version 1 can be tested locally.

---

## Phase 18 – APK build

Create a Debug APK.

Android Studio path is typically:

```text
app/build/outputs/apk/debug/app-debug.apk
```

Add instructions to README or docs:

- how to build APK
- how to copy APK to phone
- how to install APK locally

Expected result:

- User can install the app locally on Android.

---

## Phase 19 – Release preparation

Before Version 1.0:

- update app name
- add app icon
- update version number
- update README
- update CHANGELOG
- create release notes
- confirm no debug-only text remains

Expected result:

- Project is ready for a first local release.

---

## Phase 20 – Future-proofing

Do not implement these in Version 1, but keep structure ready for:

- Google Play
- more lessons
- more levels
- web version
- cloud sync
- AI conversation practice

Expected result:

- Version 1 stays simple but can grow later.

---

# 4. Suggested GitHub Issues

Codex may implement the app as separate GitHub issues.

## Issue 1

Set up clean Android project structure.

## Issue 2

Create Kotlin data models.

## Issue 3

Add local JSON lesson files.

## Issue 4

Implement LessonRepository.

## Issue 5

Build Home Screen.

## Issue 6

Build Lesson Overview Screen.

## Issue 7

Build Dialogue Screen.

## Issue 8

Implement Text-to-Speech.

## Issue 9

Implement progress storage.

## Issue 10

Build Quiz Engine.

## Issue 11

Build Result Screen.

## Issue 12

Build Progress Screen.

## Issue 13

Build Settings Screen.

## Issue 14

Improve UI styling.

## Issue 15

Add error handling.

## Issue 16

Test on emulator.

## Issue 17

Test on physical phone.

## Issue 18

Generate Debug APK.

## Issue 19

Update documentation.

## Issue 20

Prepare Version 1.0 release.

---

# 5. Acceptance Criteria for Version 1

Version 1 is acceptable when:

- the app builds in Android Studio
- APK can be installed locally
- 10 lessons are visible
- each lesson has 10 dialogues
- Danish → European Portuguese is used
- quiz works
- progress is saved
- pronunciation works or fails gracefully
- app works offline
- app does not crash during normal use

---

# 6. Recommended First Codex Prompt

Use this prompt when asking Codex to start implementation:

```text
Repository: nenolinkdk/nenoling-da-po

Read:
docs/LearnPortuguese_v1_Specification.md
docs/CODEX_IMPLEMENTATION_GUIDE.md

Implement Phase 1 only:
- inspect the existing Android project
- make sure Gradle sync/build works
- create or clean the recommended folder structure
- do not implement all features yet
- do not remove working functionality unless necessary
- update README or CHANGELOG with what was changed

Commit the result to a new branch:
feature/phase-01-project-setup
```

---

# 7. Recommended Second Codex Prompt

```text
Implement Phase 2 and Phase 3:
- create Kotlin data models for Lesson, Dialogue, Phrase, VocabularyItem, GrammarNote, QuizQuestion and UserProgress
- prepare the app for local JSON lesson data
- do not build UI yet except if needed for compilation
- keep code simple and well structured
- update documentation if needed

Commit to:
feature/phase-02-data-model
```

---

# 8. Recommended Android Studio Workflow

After Codex completes a phase:

1. Open Android Studio.
2. Pull latest changes from GitHub.
3. Sync Gradle.
4. Run the app.
5. Test the new feature.
6. Note any error messages.
7. Ask Codex to fix only those errors.
8. Build APK when stable.

---

# 9. Important Development Rule

Do not ask Codex to build everything at once.

Use phases.

One phase at a time.

Test in Android Studio after each phase.

This reduces errors and makes the project easier to control.

---

End of implementation guide.
