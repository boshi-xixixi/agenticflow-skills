# Flutter Clean Architecture Guidelines

This document defines the standard project structure and architectural patterns for enterprise Flutter applications.

## 1. Core Principles

- **Separation of Concerns**: UI, Business Logic, and Data layers must be decoupled.
- **Dependency Injection**: Use Riverpod for DI.
- **Unidirectional Data Flow**: Data flows down, events flow up.
- **Immutability**: Use `freezed` for all data models and states.

## 2. Project Structure

```
lib/
├── main.dart                          # App Entry Point
│
├── presentation/                      # UI Layer (Widgets & Pages)
│   ├── pages/                         # Full Screens
│   │   ├── [feature]/
│   │   │   ├── [feature]_page.dart
│   │   │   └── [feature]_screen.dart
│   │   │
│   ├── widgets/                       # Reusable Components
│   │   ├── common/                    # Global shared widgets
│   │   │   ├── app_button.dart
│   │   │   └── app_card.dart
│   │   │
│   │   └── [feature]/                 # Feature-specific widgets
│   │       └── [widget_name].dart
│   │
│   └── providers/                     # UI-Specific Providers (ViewControllers)
│       └── [feature]_provider.dart
│
├── business_logic/                    # Domain Layer (Logic)
│   ├── notifiers/                     # StateNotifiers / AsyncNotifiers
│   │   └── [entity]_notifier.dart
│   │
│   └── services/                      # Pure Business Services
│       └── [service]_service.dart
│
├── data/                              # Data Layer (Repositories & Sources)
│   ├── datasources/
│   │   ├── remote/                    # API Calls
│   │   │   └── [entity]_remote_data_source.dart
│   │   │
│   │   └── local/                     # Database / SharedPrefs
│   │       └── [entity]_local_data_source.dart
│   │
│   ├── models/                        # DTOs & Models (Freezed)
│   │   └── [entity]_model.dart
│   │
│   ├── repositories/                  # Repository Implementations
│   │   └── [entity]_repository.dart
│   │
│   └── services/                      # API Client Config
│       └── [entity]_api_client.dart
│
├── core/                              # Shared Utilities & Config
│   ├── constants/
│   │   ├── app_constants.dart
│   │   └── api_constants.dart
│   │
│   ├── theme/
│   │   ├── app_theme.dart
│   │   └── text_theme.dart
│   │
│   ├── utils/
│   │   ├── extensions.dart
│   │   └── validators.dart
│   │
│   └── errors/
│       ├── exceptions.dart
│       └── failures.dart
│
└── config/                            # App Configuration
    ├── routes.dart
    ├── app_config.dart
    └── environment.dart
```

## 3. Layer Responsibilities

### Presentation Layer
- **Responsibility**: Render UI, handle user input.
- **Rules**:
  - NO business logic.
  - Watch Providers for state.
  - Dispatch events to Notifiers/Controllers.

### Business Logic Layer
- **Responsibility**: Manage state, execute business rules.
- **Rules**:
  - Platform agnostic (no UI imports like `material.dart` if possible).
  - Interact with Repositories.
  - Expose `AsyncValue<State>`.

### Data Layer
- **Responsibility**: Fetch and persist data.
- **Rules**:
  - **DataSources**: Raw data access (HTTP, SQL).
  - **Repositories**: Coordinate data sources, handle exceptions, map DTOs to Domain models.
  - **Models**: `fromJson`, `toJson`.

## 4. Testing Strategy
- **Unit**: Business Logic & Data Layers.
- **Widget**: Presentation Layer.
- **Integration**: End-to-End flows.
