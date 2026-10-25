# NFAuth Android test app

This is Android source code, not a compiled APK. It has not been compiled or device-tested here. It opens the live NFAuth website in a WebView. Internet is required. Existing server security and privacy risks are unchanged. File selection is supported; direct in-app camera capture, push notifications and offline account access are not implemented. SSL errors are not bypassed.

## Build from an Android phone

1. Sign in at https://github.com and create a new repository named NFAuth-Android. A public repository is suitable for this source only: there are no signing secrets or database credentials in this project. Never upload your htdocs folder, database files, passwords or real student records.
2. Extract this ZIP on your phone. Upload the project CONTENTS to the repository root, not inside an extra NFAuth-Android folder. The root must contain settings.gradle, build.gradle, app/ and .github/.
3. Use Chrome Desktop site if the upload or Actions controls are hidden. GitHub's browser uploader may not preserve directories reliably on a phone. If needed, create files using Add file > Create new file and enter the complete paths from this ZIP, including .github/workflows/build.yml. Upload the PNG icon into app/src/main/res/mipmap-hdpi/ separately. Keep all paths exactly as supplied.
4. Open Actions > Build Android test APK > Run workflow. Enable Actions if asked. The workflow downloads Android build tools and compiles the app. Hosted build availability and usage limits depend on your account and GitHub's terms.
5. When it succeeds, open the run and download the NFAuth-test-APK artifact. Extract its ZIP to get app-debug.apk.
6. Open app-debug.apk on your Android phone. Allow installation from the browser or file manager when Android asks. Do not disable Play Protect. If Android blocks it, inspect the warning rather than bypassing it blindly.
7. Test login/logout, session expiry, OTP, attendance, all approval screens and selecting a workplace/ID image before distributing anything.

If the build fails, send the failed step's error text, not any passwords or signing files.

## Test build limitations

The workflow creates a debug-signed test APK. Do not publish it for general download. Rebuilt debug APKs can have different signing keys, preventing updates over an earlier installation. Before distribution, create a release signing key, keep it private and securely backed up, and build a release APK. The same signing identity must be used for future updates. Store publishing would require a release AAB and additional policy work.

## Website companion update

Upload the separate NFAuth-Website-Native-App-Fix.zip contents to htdocs, replacing index.html and assets/pwa.js. This hides the PWA download popup inside the Android app via its NFAuthAndroid user-agent marker. This marker is only a UI hint, not an authorization mechanism. Browser visitors still see the existing PWA prompt; it does not yet download the APK. Change that prompt only once a tested release APK is available.
