# ketabk

Flutter application for browsing books powered by the Google Books API.

## Features

- Browse featured and newest free eBooks
- Book details view with cover image, rating, and preview action
- Search UI (work in progress)

## Tech Stack

- **Flutter** (Dart)
- **State Management**: `flutter_bloc` (Cubit)
- **Networking**: `dio`
- **Routing**: `go_router`
- **Service Locator / DI**: `get_it`
- **Functional Error Handling**: `dartz`
- **Models / Equality**: `equatable`
- **UI Utilities**: `google_fonts`, `font_awesome_flutter`
- **Images**: `cached_network_image`
- **External Links**: `url_launcher`

## Project Structure

The codebase follows a feature-first structure:

```
lib/
  Features/
    Splash/
    home/
    search/
  core/
    errors/
    utils/
    widgets/
  constants.dart
  main.dart
```

High-level flow:

- `main.dart` sets up dependencies and starts the app.
- `core/utils/service_locator.dart` registers core services and repositories.
- `core/utils/app_router.dart` defines navigation routes.
- Each feature contains its own data + presentation layers.

## Getting Started

### Prerequisites

- Flutter SDK (matching the SDK constraint in `pubspec.yaml`)
- Android Studio / VS Code with Flutter & Dart plugins

### Install Dependencies

```bash
flutter pub get
```

### Run

```bash
flutter run
```

### Analyze

```bash
flutter analyze
```

## Configuration

This app consumes the Google Books API via `core/utils/api_service.dart`.

- No API key is required for basic Google Books API usage.
- If you add an API key in the future, do **not** hardcode it. Use
  platform-specific configuration or environment-based injection.

## Common Issues

### Imports still refer to a different package name

This project package name is `ketabk` (see `pubspec.yaml`). If you see imports
like `package:bookly/...`, update them to `package:ketabk/...`.

### `flutter pub get` succeeds but `flutter analyze` reports missing packages

Make sure the dependency is listed under `dependencies:` in `pubspec.yaml`,
then re-run:

```bash
flutter clean
flutter pub get
```

## License

This project is currently unlicensed. Add a license file if you plan to share
or distribute it.
