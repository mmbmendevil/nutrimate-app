# Project Structure

This document describes the current NutriMateApp structure as it exists today. It does not propose a folder restructure or architecture change.

## Root Directory

```text
NutriMateApp/
├── app/
├── gradle/
├── build.gradle.kts
├── settings.gradle.kts
├── gradle.properties
├── gradlew
├── gradlew.bat
├── README.md
├── SETUP_GUIDE.md
├── PROJECT_STRUCTURE.md
├── CONTRIBUTING.md
├── CHANGELOG.md
└── LICENSE
```

- `app/` contains the Android application module.
- `gradle/` contains the Gradle Wrapper files and version catalog.
- `build.gradle.kts` is the root Gradle build file.
- `settings.gradle.kts` defines the project name and includes the `app` module.
- `gradle.properties` contains Gradle and Android build properties.
- `gradlew` and `gradlew.bat` allow the project to build without a globally installed Gradle version.
- `Group 2 - NutriMate - Weekly Sprint Plan.xlsx` is preserved as project planning material.

## App Module

```text
app/
├── build.gradle.kts
├── proguard-rules.pro
└── src/
    ├── main/
    ├── test/
    └── androidTest/
```

- `app/build.gradle.kts` configures the Android app module, SDK versions, Java compatibility, and dependencies.
- `app/proguard-rules.pro` is available for release build optimization rules.
- `app/src/main/` contains production app code and resources.
- `app/src/test/` contains local JVM test code.
- `app/src/androidTest/` contains instrumented Android test code.

## Main Source Set

```text
app/src/main/
├── AndroidManifest.xml
├── java/com/example/nutrimateapp/
└── res/
```

- `AndroidManifest.xml` declares app permissions, launcher activity, theme, icon, and registered Activities.
- `java/com/example/nutrimateapp/` contains the Java source code.
- `res/` contains layouts, drawables, strings, themes, animations, XML configuration, launcher assets, and sample nutrition data.

## Java Package Organization

```text
com/example/nutrimateapp/
├── Birthday.java
├── Complete.java
├── ForgotPassword.java
├── HealthDisclaimer.java
├── HeightActivity.java
├── HowActiveAreYou.java
├── LGS.java
├── LifestylePace.java
├── Login.java
├── LogMeals.java
├── MainActivity.java
├── Name.java
├── Personalize.java
├── PrimaryGoal.java
├── Result.java
├── Sex.java
├── Signup.java
├── Weight.java
├── database/
└── model/
```

The app currently uses an Activity-per-screen pattern. Each Activity is responsible for one part of the login, onboarding, calculation, or meal tracking flow.

### Main Activities

- `Login.java` is the launcher screen and handles prototype login navigation.
- `Signup.java` and `ForgotPassword.java` provide account-related prototype screens.
- `MainActivity.java`, `HealthDisclaimer.java`, `Personalize.java`, and `LGS.java` guide the user into onboarding.
- `Name.java`, `Birthday.java`, `Sex.java`, `HeightActivity.java`, `Weight.java`, `PrimaryGoal.java`, `HowActiveAreYou.java`, and `LifestylePace.java` collect user profile and goal information.
- `Complete.java` calculates calorie and macronutrient targets, saves profile information, and transitions to meal logging.
- `Result.java` displays stored profile and target nutrition information.
- `LogMeals.java` handles meal image selection, simulated detection, portion entry, and progress display.

## Database Layer

```text
database/
├── AppDatabase.java
└── UserProfileDao.java

model/
└── UserProfile.java
```

- `UserProfile.java` defines the Room entity for saved user profile information.
- `UserProfileDao.java` defines database insert and query operations.
- `AppDatabase.java` creates the Room database instance named `nutrimate_db`.

The current implementation uses Room for structured profile storage and SharedPreferences for temporary onboarding values and nutrition targets.

## Resource Organization

```text
res/
├── anim/
├── drawable/
├── layout/
├── mipmap-*/
├── raw/
├── values/
├── values-night/
└── xml/
```

- `layout/` contains XML screen layouts and dialog layouts.
- `drawable/` contains icons, backgrounds, images, and shape drawables.
- `anim/` contains animation XML resources.
- `values/` contains app strings, colors, styles, and themes.
- `values-night/` contains night-mode theme resources.
- `mipmap-*` contains launcher icon resources.
- `raw/` contains the sample nutrition CSV file.
- `xml/` contains backup and data extraction configuration.

## Current App Flow

The high-level navigation flow is:

```text
Login
  -> MainActivity
  -> HealthDisclaimer
  -> Personalize
  -> LGS
  -> Birthday
  -> Name
  -> Sex
  -> HeightActivity
  -> Weight
  -> PrimaryGoal
  -> HowActiveAreYou
  -> LifestylePace
  -> Complete
  -> LogMeals
```

Some screens can also navigate to related account or result screens depending on user interaction.

## Data Flow

1. The user enters profile and goal information across onboarding Activities.
2. Temporary values are stored in `SharedPreferences` under `NutriMatePrefs`.
3. `Complete.java` reads the saved onboarding values.
4. The app calculates age, BMR, TDEE, calorie target, and macronutrient targets.
5. Nutrition targets are saved back to `SharedPreferences`.
6. User profile information is saved to Room through `AppDatabase` and `UserProfileDao`.
7. `LogMeals.java` reads target values from `SharedPreferences` and updates progress indicators as meals are added.
8. `Result.java` reads stored profile information from Room and nutrition targets from `SharedPreferences`.

## Build Configuration

- Root build file: `build.gradle.kts`
- App build file: `app/build.gradle.kts`
- Version catalog: `gradle/libs.versions.toml`
- Gradle wrapper: `gradle/wrapper/gradle-wrapper.properties`

Important current build values:

- Namespace: `com.example.nutrimateapp`
- Application ID: `com.example.nutrimateapp`
- Compile SDK: `35`
- Target SDK: `35`
- Minimum SDK: `24`
- Java compatibility: `JavaVersion.VERSION_11`
