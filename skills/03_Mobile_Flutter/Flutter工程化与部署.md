---
name: Flutter DevOps & Deployment
description: Best practices for Flutter project structure, flavors, CI/CD pipelines, and app store distribution.
---

# Flutter DevOps & Deployment

Guide to professionalizing Flutter development through automation, environment management, and streamlined deployment.

## Project Organization

### 1. Flavors (Environments)
- **Dev**: Connects to staging API, has debug banners.
- **Prod**: Connects to production API, optimized for performance.
- **Tools**: Use `flutter_flavorizr` or native configurations (iOS Schemes / Android Product Flavors).

### 2. Dependency Management
- **Strict Versioning**: Use specific versions in `pubspec.yaml` for critical packages.
- **Internal Packages**: Split large projects into multiple local packages in a `packages/` directory to improve build times and modularity.

## CI/CD Pipeline

### 1. Verification (On every PR)
- Run `flutter analyze` to check for linting issues.
- Run `flutter test` to ensure no regressions.
- Check formatting with `dart format --output=none --set-exit-if-changed .`.

### 2. Build Automation
- **GitHub Actions / GitLab CI**: Use official Flutter actions to build `.apk`, `.aab`, and `.ipa`.
- **Fastlane**: Automate screenshot generation and uploading to Google Play Store and Apple App Store.

## Distribution

### 1. Android
- **App Bundles (AAB)**: Always distribute via AAB for smaller download sizes.
- **Obfuscation**: Use `--obfuscate --split-debug-info` to protect code.

### 2. iOS
- **TestFlight**: Automated uploads for internal testing.
- **App Store Connect**: Use Fastlane to manage metadata and submissions.

## Monitoring

- **Crashlytics**: Integrate Firebase Crashlytics to track runtime errors.
- **Analytics**: Use Google Analytics for Firebase to track user behavior.
- **Error Boundaries**: Implement a global error handler using `FlutterError.onError` and `PlatformDispatcher.instance.onError`.
