# Construction Daily Tracker

> A modern, complete payroll management solution for the construction industry, built with Kotlin Multiplatform and working 100% offline

[![Kotlin](https://img.shields.io/badge/Kotlin-2.1.0-blue.svg)](https://kotlinlang.org)
[![Compose Multiplatform](https://img.shields.io/badge/Compose-1.9.0-green.svg)](https://www.jetbrains.com/lp/compose-multiplatform/)
[![Room](https://img.shields.io/badge/Room-2.6.1-orange.svg)](https://developer.android.com/training/data-storage/room)

---

## APK download: [Link](https://drive.google.com/drive/folders/1PtZLVo6KCa1w9JP4mgLfaEJYqMlMlMFC?usp=sharing)

## About the Project

Managing payroll in construction is tricky, especially when you need to handle multiple job sites and track worked days with precision. **Construction Daily Tracker** tackles these challenges with a local, offline-first solution.

Whether you're managing a small crew or overseeing multiple sites, this app helps you:

Track employees across different job sites and roles
Record daily adjustments (overtime, absences, bonuses)
Automatically calculate payroll with precision
Generate monthly reports from the 6th to the 5th
Keep a full history of all changes
**Work 100% offline — all data stays on your phone**

---

## Key Features

### Payroll Calculation
- **Automatic business day calculation** excluding weekends
- **Dynamic adjustments** for overtime, absences, and bonuses
- **Real-time updates** when adjustments are added or removed
- **Financial precision** using BigDecimal for monetary values

### 📱 Local & Offline App
- **Local database** with Room/SQLite
- **No internet required** — works completely offline
- **Secure data** stored on device
- **Modern UI** built with Compose Multiplatform
- **Shared business logic** across platforms

### Secure & Private
- **Local data** — everything stays on your device
- **Encrypted storage** for sensitive preferences
- **No data sent** to external servers
- **Test coverage** following TDD principles

### Multi-Site Management
- Track multiple job sites simultaneously
- Assign employees to different roles
- Monitor work across several projects
- Generate site-specific reports

---

## Quick Start

### Prerequisites

- **Android Studio** (latest version)
- **JDK 11** or higher
- **Android device** or emulator (API 24+)

### Install the App

#### Option 1: Download Pre-built APK
1. Navigate to `composeApp/build/outputs/apk/debug/`
2. Transfer `composeApp-debug.apk` to your device
3. Enable "Install from unknown sources" in settings
4. Install the APK

#### Option 2: Build from Source

```bash
# Clone the repository
git clone https://github.com/seu-usuario/construction-daily-tracker/
cd construction-daily-tracker

# Build the debug APK
./gradlew :composeApp:assembleDebug

# APK will be at: composeApp/build/outputs/apk/debug/composeApp-debug.apk

# Install via ADB (optional)
adb install composeApp/build/outputs/apk/debug/composeApp-debug.apk
```

### Run Tests

```bash
# Run all tests
./gradlew test

# Run shared module tests only
./gradlew :shared:test

---

## Architecture

This project follows a **clean, modular architecture** with local storage:

```
construction-daily-tracker/
├── shared/                        # Platform-agnostic business logic
│   └── src/
│       ├── commonMain/kotlin/
│       │   ├── model/             # Data models (Employee, WorkMonth, DayRecord)
│       │   └── utils/             # WorkDaysCalculator, helpers
│       ├── androidMain/
│       └── jvmMain/
└── composeApp/                    # Android application
    └── src/
        ├── commonMain/kotlin/
        │   ├── navigation/        # NavigationState, Screen
        │   ├── ui/screens/        # All UI screens
        │   └── i18n/              # String resources
        └── androidMain/kotlin/
            ├── database/          # AppDatabase (Room)
            │   ├── dao/           # DAO interfaces
            │   └── entities/      # Room entities
            └── repository/        # Local repository implementations
```

### Tech Stack

**Android:**
- **Compose Multiplatform** - UI
- **Room Database** - Local persistence
- **SQLite** - Database
- **ViewModel** - State management

**Shared:**
- **Kotlin Serialization**
- **Kotlin Multiplatform**
