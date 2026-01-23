---
name: Flutter Clean Architecture
description: Implement Clean Architecture in Flutter using BLoC/Riverpod, Repository pattern, and Use Cases to build scalable, testable, and maintainable applications. Use when starting large-scale Flutter projects or refactoring legacy codebases.
---

# Flutter Clean Architecture

Master the implementation of Clean Architecture principles in Flutter to create robust, testable, and scalable mobile applications.

## When to Use This Skill

- Starting a new medium-to-large scale Flutter project
- Refactoring an existing codebase that has become hard to maintain
- Needing to separate business logic from UI code strictly
- Implementing comprehensive unit and integration testing
- Working in a team where separation of concerns is critical

## Core Concepts

### 1. Layers
- **Presentation Layer**: UI (Widgets) and State Management (BLoC/Cubit/Riverpod). Only handles "how things look".
- **Domain Layer**: The heart of the app. Contains Entities (Pure Dart classes), Use Cases (Business Logic), and Repository Interfaces. No Flutter dependencies here!
- **Data Layer**: Implementations of Repository Interfaces. Handles API calls (Retrofit/Dio), Local Storage (Hive/Drift), and DTOs (Data Transfer Objects).

### 2. Dependency Injection (DI)
- Use `get_it` and `injectable` to manage dependencies.
- Ensure Use Cases are injected into Blocs/Providers.
- Ensure Repositories are injected into Use Cases.

### 3. Data Flow
`UI -> BLoC -> Use Case -> Repository (Interface) -> Repository (Impl) -> Data Source -> API/DB`

## Implementation Steps

1.  **Define Entities**: Create pure Dart classes in the Domain layer representing your business objects.
2.  **Define Repository Interfaces**: Abstract classes in the Domain layer defining what data operations are needed.
3.  **Implement Use Cases**: Classes in the Domain layer that encapsulate a specific business rule (e.g., `LoginUser`, `GetProducts`).
4.  **Implement Data Models**: DTOs in the Data layer that extend Entities and handle JSON serialization (using `json_serializable`).
5.  **Implement Repositories**: Concrete classes in the Data layer that fetch data from sources and return Entities.
6.  **Build Presentation**: Create Widgets and BLoCs that consume Use Cases.

## Best Practices

- **Strict Boundaries**: The Domain layer should NEVER import `flutter` or `data` layer packages.
- **Mappers**: Use mapper classes to convert DTOs to Entities and vice versa.
- **Error Handling**: Use `Either<Failure, Success>` (using `fpdart` or `dartz`) type for return values in Repository/Use Cases to handle errors functionally.
- **Testing**:
    - **Domain**: Pure unit tests (no mocks needed usually, or mock repos).
    - **Data**: Mock data sources.
    - **Presentation**: Widget tests and BLoC tests.
