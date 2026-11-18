# DARK EDITOR — Flutter starter project

A dark / neon-purple cross-platform video editor starter. Android is the first build target; the GitHub Actions workflow also generates Flutter platform folders for iOS, web, Windows, macOS and Linux.

## What is included now

- Premium dark + neon-purple home screen and tool navigation.
- Multi-video selection using the Android system file picker (`allowMultiple: true`). No arbitrary app-side clip count cap; actual capacity depends on device storage and performance.
- Selected clip list, remove-from-selection control, and a visible Continue check button.
- Editor workspace with local video preview, clip switching, section/subsection tool menus, and a starter timeline-style layout.
- HD Enhance is gated behind a sign-in screen placeholder.
- GitHub Actions workflow to build a debug APK in the cloud.

## Important: honest feature status

This is a runnable **starter UI and project foundation**, not a finished professional editor. The buttons and menus for AI Cut Out, HD Enhance, masks, animation/keyframes, filters, effects, motion blur, audio processing, freeze-frame, capture, export/rendering, and templates currently show the intended workflow but need real editing/rendering engines and (for AI/auth) backend services. The app does not yet render edited videos or export a final movie. Do not publish it as a finished editor until these engines, permissions, device testing, privacy policy and store requirements are completed.

## Upload from an Android phone (no PC)

1. Download and extract `DARK_EDITOR_Full_Project.zip` on your phone.
2. Open your GitHub repository `dark-editor` in Chrome and sign in.
3. Tap **Add file → Upload files**. Select the extracted project files and folders, keeping the folder structure. If the Android picker hides the `.github` folder, upload the visible project files first, then create the workflow manually using step 4.
4. To add the build workflow manually: in GitHub tap **Add file → Create new file**. Enter this exact filename: `.github/workflows/android-apk.yml`. Paste the workflow from `GITHUB_WORKFLOW_SETUP.md`, then commit it to `main`.
5. Commit all uploaded files to the `main` branch.
6. Open the repository's **Actions** tab. Choose **Build DARK EDITOR Android APK**. If it has not started automatically, tap **Run workflow**.
7. Wait for the run to finish with a green check. Open the run, scroll to **Artifacts**, and download `dark-editor-debug-apk`. Extract it; `app-debug.apk` is the test build.

## Build notes

- This workflow produces a **debug APK** for testing. A Play Store release requires a properly signed release build, secure signing-key setup, testing, privacy disclosures and Google Play policy compliance.
- The 100–150 MB target is not guaranteed. Final size depends on codecs, native libraries, AI models and included assets. Large AI models should generally be downloaded on demand rather than bundled.
- The source is Flutter/Dart. iOS builds require Apple tooling/signing and cannot be produced as an installable iOS app from this Android-only workflow. Windows/macOS/Linux builds need their own runners and platform testing.
