# 🎬 Movie App

A premium, feature-rich **Movie Discovery & Browsing** application built with **Flutter**. Designed around **Clean Architecture** principles and robust software engineering patterns, the app features dynamic movie listings, secure authentication, dependency injection, and state management using the BLoC pattern.

---

## ✨ Features

- **📺 Immersive Movie Catalog**: Browse trending movies, detailed lists, and upcoming releases grouped into distinct "Watch Now" (featured carousel) and "Available Now" sections.
- **🛡️ Clean Architecture (Domain-Driven Design)**: Modules (such as `auth`) are organized into strict layers:
  - **Data**: Implements data sources, models, and repositories.
  - **Domain**: Expresses core business logic entities, use cases, and repository interfaces.
  - **Presentation**: Houses BLoCs and UI widgets.
- **⚙️ BLoC State Management**: Employs `flutter_bloc` for robust, event-driven state tracking at the feature layer, alongside `provider` for global settings.
- **💉 Automated Dependency Injection**: Integrates `get_it` and `injectable` for compiling dependencies through automatic code-generation.
- **🌐 Network & Error Resilience**:
  - Connects to a custom movie service deployment (`https://route-movie-apis.vercel.app`) using both `dio` and `http`.
  - Employs functional error handling via `dartz` (`Either` type) to safely capture and display server failures or network timeouts.
- **👤 User Profile Management**: Supports profile creation, custom avatar selection, and dynamic profile updates (`UpdateProfile`).
- **🛹 Onboarding Walkthroughs**: Guides users through app features with a modern onboarding journey (`OnBoardingScreen` & `BasicOnBoarding`).
- **🎭 Cinema Dark Styling**: A theater-like, deep dark theme styled with premium typography (`google_fonts`) and smooth UI animations.

---

## 🛠️ Tech Stack & Dependencies

Agrinova leverages several state-of-the-art packages:

- **State Management**: 
  - `flutter_bloc` — Manages event-driven feature states.
  - `provider` — Global configuration state (e.g. locale & language).
- **Dependency Injection**:
  - `get_it` — Service locator.
  - `injectable` & `injectable_generator` — Code-generation compiler for dependencies.
- **Networking & Error Handling**:
  - `dio` & `http` — REST clients for API communication.
  - `dartz` — Functional programming helper for modeling success and error paths (`Either<Failure, Success>`).
- **UI Components**:
  - `carousel_slider` — Fluid sliding banner for featured movies.
  - `google_fonts` — Premium typography rendering.
  - `animated_toggle_switch` & `toggle_switch` — Segmented option controls.
  - `icons_plus` & `flutter_svg` — Rich vector support and premium icons.
- **Local Storage**: `shared_preferences` — Configuration settings persistence.

---

## 📁 Project Directory Structure

```text
lib/
├── auth/                        # Authentications layer (Clean Architecture)
│   ├── data/                    # Data sources, models, and API clients
│   ├── domain/                  # Entities, Use Cases, and Repository interfaces
│   └── presentation/            # Auth screens, forms, and validation BLoCs
├── bloc/                        # Global state providers (e.g. LanguageProvider)
├── core/                        # Global resources and configurations
│   ├── app_const/
│   │   └── app_const.dart       # API base URLs and endpoints configuration
│   ├── app_theme/
│   │   └── app_theme.dart       # Cinema dark theme configurations
│   ├── di/
│   │   └── di.dart              # Dependency injection setup (GetIt configureDependencies)
│   ├── errors/                  # Error and network Failure models
│   ├── routes/
│   │   └── app_routes.dart      # Navigation router registry (AppRoutes)
│   ├── validators.dart          # Form input validation rules
│   └── widgets/                 # Reusable fields and inputs (AppFormField)
├── database/                    # Offline database services
├── l10n/                        # Multi-language localizations (ARB translation bundles)
├── SharedPreferences/           # App settings persistence wrapper classes
├── ui/                          # General UI pages
│   ├── OnBoarding/              # App introductory slides
│   ├── Register/                # User register page
│   ├── UpdateProfile/           # Account settings editing page
│   ├── forget_password_screen/  # Password recovery portal
│   ├── login_screen/            # Credentials entry sign-in page
│   └── home_screen/             # Movie hub dashboard container (sliders + grids)
└── main.dart                    # App launcher initializing DI dependencies and theme routes
```

---

## 🚀 Getting Started

Follow these steps to run the application on your computer:

### 1. Prerequisites

Ensure you have the [Flutter SDK](https://docs.flutter.dev/get-started/install) installed and configured on your system.

```bash
flutter --version
```

### 2. Clone the Repository

```bash
git clone https://github.com/nda-mohamed/movie_app.git
cd movie_app
```

### 3. Install Dependencies

Fetch all dependencies:

```bash
flutter pub get
```

### 4. Run Code Generation

Since the project uses `injectable` for dependency wiring, compile the service locator files:

```bash
flutter pub run build_runner build --delete-conflicting-outputs
```

*(Note: Run this command whenever you change or register new injectable classes.)*

### 5. Run the Application

Build and run on your target platform:

```bash
flutter run
```
