# Feature Generation Template

Use this structure when asked to "Generate a Feature" or "Create a module".

## Directory Structure

```
features/[feature_name]/
├── data/
│   ├── datasources/
│   │   └── [feature]_remote_data_source.dart
│   ├── models/
│   │   └── [feature]_model.dart
│   └── repositories/
│       └── [feature]_repository_impl.dart
├── domain/
│   └── repositories/
│       └── [feature]_repository.dart
├── presentation/
│   ├── pages/
│   │   └── [feature]_page.dart
│   ├── widgets/
│   │   └── [feature]_widget.dart
│   └── providers/
│       └── [feature]_provider.dart
└── test/
    ├── [feature]_repository_test.dart
    └── [feature]_page_test.dart
```

## Checklist for New Features

1.  [ ] Define the Domain Model (Entity).
2.  [ ] Create the Data Model (Freezed DTO) with `fromJson`.
3.  [ ] Define the Repository Interface (Domain).
4.  [ ] Implement the RemoteDataSource (API calls).
5.  [ ] Implement the Repository (Data Layer).
6.  [ ] Create the Notifier/Provider (Business Logic).
7.  [ ] Build the UI Page and Widgets.
8.  [ ] Write Unit Tests for Repository & Notifier.
9.  [ ] Write Widget Tests for the Page.
