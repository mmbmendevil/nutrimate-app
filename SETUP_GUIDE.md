# Setup Guide

This guide explains how to set up, build, and run NutriMateApp from a clean local checkout.

## Prerequisites

Install the following before opening the project:

- Android Studio, recent stable version recommended.
- JDK compatible with Java 11.
- Android SDK Platform 35.
- Android SDK Build Tools installed through Android Studio.
- Git.

The project uses the included Gradle Wrapper, so you do not need to install Gradle manually.

## Clone the Repository

```bash
git clone https://github.com/your-username/NutriMateApp.git
cd NutriMateApp
```

Replace `your-username` with the GitHub account or organization that hosts the repository.

## Open in Android Studio

1. Open Android Studio.
2. Select **Open**.
3. Choose the `NutriMateApp` project folder.
4. Wait for Gradle sync to finish.
5. If Android Studio prompts you to install missing SDK packages, accept the installation.

## Gradle Sync

Android Studio should automatically sync the project. If it does not:

1. Open **File > Sync Project with Gradle Files**.
2. Wait for dependency resolution to complete.
3. Confirm that the `app` module appears in the project tree.

## SDK Setup

The app module is configured with:

- `compileSdk = 35`
- `targetSdk = 35`
- `minSdk = 24`

To install SDK Platform 35:

1. Open **Tools > SDK Manager**.
2. Select **Android SDK Platform 35**.
3. Apply the changes.
4. Let Android Studio install the selected packages.

## Emulator Setup

1. Open **Tools > Device Manager**.
2. Select **Create Device**.
3. Choose a phone profile, such as Pixel 6 or Pixel 7.
4. Select a system image compatible with API 35, or another installed API level supported by the app.
5. Finish creating the emulator.
6. Start the emulator before running the app.

You can also run the app on a physical Android device with USB debugging enabled.

## Build Commands

Windows:

```bash
gradlew.bat assembleDebug
```

macOS/Linux:

```bash
./gradlew assembleDebug
```

The debug APK will be generated under:

```text
app/build/outputs/apk/debug/
```

## Run Tests

Local unit tests:

Windows:

```bash
gradlew.bat test
```

macOS/Linux:

```bash
./gradlew test
```

Instrumented Android tests require an emulator or connected device:

Windows:

```bash
gradlew.bat connectedAndroidTest
```

macOS/Linux:

```bash
./gradlew connectedAndroidTest
```

## Run the App

From Android Studio:

1. Select the `app` configuration.
2. Select an emulator or connected device.
3. Click **Run**.

The launcher activity is `Login`.

## Troubleshooting

### Gradle sync fails

- Confirm that the Android Gradle Plugin and Gradle Wrapper versions are being used from the project files.
- Check your internet connection for dependency downloads.
- Run **File > Invalidate Caches** in Android Studio if sync state appears stale.

### Missing SDK error

- Open **Tools > SDK Manager**.
- Install Android SDK Platform 35.
- Sync the project again.

### JDK version issue

- In Android Studio, open **Settings > Build, Execution, Deployment > Build Tools > Gradle**.
- Use Android Studio's bundled JDK or another Java 11 compatible JDK.

### Emulator does not start

- Confirm virtualization is enabled in your BIOS/UEFI.
- Use Device Manager to create a new emulator.
- Try a lower-resolution emulator profile if your machine has limited resources.

### Build output appears stale

Run a clean build:

Windows:

```bash
gradlew.bat clean assembleDebug
```

macOS/Linux:

```bash
./gradlew clean assembleDebug
```

### Dependency download problems

- Confirm that `google()` and `mavenCentral()` are reachable from your network.
- Retry Gradle sync.
- If using a school or company network, check whether Gradle or Maven downloads are blocked.
