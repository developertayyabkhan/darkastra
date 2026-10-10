# DARKGPT - Native Android App

Is project mei aapki website ka design (index.html, style.css) aur logic/backend
(script.js -> n8n webhook + BYO API keys) bilkul same `www/` folder mei hai.
Capacitor isko asli Android app (APK) mei wrap karta hai.

## Requirements (apne PC par)
- Node.js 18+
- Android Studio (SDK + JDK 17 ke saath)

## Steps
1. `npm install`
2. `npx cap add android`
3. `android-permissions.txt` wali 3 permission lines AndroidManifest.xml mei add karein
4. `npx cap sync android`
5. `npx cap open android`  -> Android Studio mei Build > Build APK(s)
   ya terminal se: `cd android && ./gradlew assembleDebug`
   APK yaha milegi: android/app/build/outputs/apk/debug/app-debug.apk

## Website code update karne k baad
`www/` mei files badlein, phir `npx cap sync android` chalayein.

## Dhyan dein
- Capacitor ka CapacitorHttp plugin on hai taa k n8n webhook par CORS ka masla na aaye.
- Voice call (MediaRecorder + mic) Android WebView mei chalti hai.
- Mic button wala "voice input" (webkitSpeechRecognition) Android WebView mei support nahi hota,
  isliye app mei woh button khud hide ho jata hai (aapka code pehle se aisa karta hai).
  Voice call wala feature poora kaam karega.

## PC ke baghair APK (GitHub se, free)
1. github.com par naya repository banayein
2. Is project ke saare files (hidden `.github` folder samet) upload karein
3. Repository mei Actions tab kholein > "Build DARKGPT APK" > Run workflow
4. 5-8 minute baad run khol kar neeche Artifacts se `DARKGPT-apk` download karein, zip kholein, `app-debug.apk` phone mei install karein
