Create this file in GitHub as `.github/workflows/android-apk.yml` if your Android file picker does not show hidden `.github` folders:

```yaml
name: Build DARK EDITOR Android APK
on:
  workflow_dispatch:
  push:
    branches: [ main, master ]
permissions:
  contents: read
  actions: read
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout source
        uses: actions/checkout@v4
      - name: Set up Java
        uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'
      - name: Set up Flutter
        uses: subosito/flutter-action@v2
        with:
          channel: stable
          cache: true
      - name: Generate platform folders
        run: flutter create --platforms=android,ios,web,windows,macos,linux .
      - name: Get packages
        run: flutter pub get
      - name: Build debug APK
        run: flutter build apk --debug
      - name: Upload APK artifact
        uses: actions/upload-artifact@v4
        with:
          name: dark-editor-debug-apk
          path: build/app/outputs/flutter-apk/app-debug.apk
          if-no-files-found: error
```
