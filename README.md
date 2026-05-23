# NutriMateApp

NutriMateApp is an Android nutrition companion prototype that helps users set up a personal profile, choose health and fitness goals, calculate calorie and macronutrient targets, and track meal progress through a mobile-first interface.

The project is prepared as a portfolio and academic showcase of Android development fundamentals, including multi-screen navigation, XML-based UI construction, local persistence, form validation, goal-based calculations, and prototype meal logging flows.

## Overview

NutriMateApp guides a user through account access, onboarding, profile personalization, activity and goal selection, and nutrition target calculation. After onboarding, the app presents a meal logging experience where users can add a meal through camera or gallery selection, enter portions, and view progress toward daily calorie and macronutrient goals.

This repository intentionally preserves the current Android architecture and implementation so the project can be reviewed, built, and extended without hidden restructuring.

## Features

- Prototype login, sign-up, and forgot-password screens.
- Guided onboarding screens for name, birthday, sex, height, weight, activity level, primary goal, and lifestyle pace.
- Health disclaimer and personalization flow before nutrition tracking.
- Calorie target calculation using profile details, activity level, and selected goal.
- Macronutrient target calculation for protein, carbohydrates, and fats.
- Local profile persistence with Room Database.
- Temporary onboarding and target storage with SharedPreferences.
- Meal logging screen with calorie and macronutrient progress indicators.
- Camera and gallery entry points for meal image selection.
- Simulated food detection flow for prototype demonstration.
- Portion input dialog for estimating meal nutrition.
- XML layouts, drawable resources, and animation resources for the app interface.

## Tech Stack

- Java
- Android SDK
- Gradle Kotlin DSL
- Android Gradle Plugin 8.8.0
- Gradle Wrapper 8.10.2
- AndroidX AppCompat
- Material Components for Android
- ConstraintLayout
- AndroidX Activity
- Room Database
- SharedPreferences
- XML layouts and drawable resources
- JUnit, AndroidX Test, and Espresso dependencies

## Project Structure

```text
NutriMateApp/
├── app/                         # Main Android application module
│   ├── build.gradle.kts          # App module build configuration
│   └── src/
│       ├── main/
│       │   ├── AndroidManifest.xml
│       │   ├── java/com/example/nutrimateapp/
│       │   │   ├── *.java        # Activity classes and app flow
│       │   │   ├── database/     # Room database and DAO
│       │   │   └── model/        # Room entity model
│       │   └── res/              # Layouts, drawables, values, animations, XML config
│       ├── test/                 # Local unit test placeholder
│       └── androidTest/          # Instrumented test placeholder
├── gradle/                       # Gradle wrapper and version catalog
├── build.gradle.kts              # Root Gradle configuration
├── settings.gradle.kts           # Project/module settings
└── gradle.properties             # Gradle and Android build properties
```

For a more detailed breakdown, see [PROJECT_STRUCTURE.md](PROJECT_STRUCTURE.md).

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/NutriMateApp.git
   cd NutriMateApp
   ```

2. Open the project in Android Studio.
3. Allow Android Studio to complete Gradle sync.
4. Install any missing Android SDK components if prompted.
5. Select an emulator or connected Android device.

For beginner-friendly setup help, see [SETUP_GUIDE.md](SETUP_GUIDE.md).

## Running the App

From Android Studio:

1. Open the project.
2. Wait for Gradle sync to finish.
3. Select the `app` run configuration.
4. Choose an emulator or physical device.
5. Click Run.

From the command line on Windows:

```bash
gradlew.bat assembleDebug
```

From the command line on macOS/Linux:

```bash
./gradlew assembleDebug
```

## Requirements

- Android Studio: recent stable version recommended.
- JDK: Java 11 compatibility is configured in the app module.
- Gradle Wrapper: 8.10.2.
- Android Gradle Plugin: 8.8.0.
- Compile SDK: 35.
- Target SDK: 35.
- Minimum SDK: 24.
- Android emulator or physical Android device for running the app.

## Architecture Overview

NutriMateApp currently uses a straightforward Activity-based Android architecture. Each major screen is implemented as a Java `Activity` with a matching XML layout under `app/src/main/res/layout`.

User onboarding data is collected across multiple screens and saved temporarily through `SharedPreferences`. When onboarding is completed, the app calculates nutrition targets and stores user profile information in a Room database through `AppDatabase`, `UserProfileDao`, and the `UserProfile` entity.

The meal logging flow reads saved target values, displays progress indicators, and supports camera/gallery-based meal entry for the prototype food detection and portion input workflow.

## Challenges & Learnings

- Designing a multi-step onboarding flow requires consistent data passing and careful handling of incomplete profile values.
- Nutrition target calculation combines user input, activity multipliers, goals, and macronutrient distribution into a practical mobile workflow.
- Local persistence with Room provides a clear path for storing structured user profile data.
- XML layouts and drawable resources remain effective for building predictable Android screens in a beginner-friendly project.
- Prototype image-based meal logging is useful for demonstrating product direction before integrating production machine learning or nutrition APIs.

## Future Improvements

- Replace prototype authentication with a secure backend or Firebase Authentication.
- Move long-running database work away from the main thread.
- Add full validation and recovery paths for incomplete onboarding data.
- Store meal history persistently instead of only showing session-based meal cards.
- Add real food recognition or barcode lookup through a production nutrition data source.
- Add automated UI tests for the onboarding and meal logging flows.
- Improve accessibility labels, contrast checks, and screen reader support.
- Add release signing configuration for production distribution.

## Repository Description

Android nutrition tracking prototype with onboarding, calorie and macronutrient goal calculation, Room persistence, and meal logging UI.

## Suggested Topics

`android`, `java`, `nutrition`, `health-app`, `room-database`, `material-design`, `gradle`, `portfolio-project`, `academic-project`

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
