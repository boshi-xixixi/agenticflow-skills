# Flutter CI/CD (GitHub Actions)

Standard workflow for automated testing and deployment.

## Workflow File (`.github/workflows/flutter.yml`)

```yaml
name: Flutter CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: subosito/flutter-action@v2
        with:
          flutter-version: '3.16.0'
          channel: 'stable'
      
      - name: Get Dependencies
        run: flutter pub get

      - name: Analyze
        run: flutter analyze

      - name: Format Check
        run: dart format --set-exit-if-changed .

      - name: Run Tests
        run: flutter test --coverage
```
