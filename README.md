# Учёт часов — мобильное приложение (Capacitor)

Приложение — это страница `www/index.html`, упакованная в Android/iOS через Capacitor.
Все данные хранятся на телефоне, интернет не нужен.

## Что понадобится
- Node.js 20+ (https://nodejs.org)
- Для Android: Android Studio (https://developer.android.com/studio)
- Для iPhone: Mac с Xcode и аккаунт Apple Developer (для установки на реальное устройство)

## Android: сборка APK
```bash
npm install @capacitor/core @capacitor/cli @capacitor/android
npx cap add android
npx cap sync android
npx cap open android
```
В Android Studio: Build → Build Bundle(s) / APK(s) → Build APK(s).
Готовый файл лежит в `android/app/build/outputs/apk/debug/app-debug.apk` —
скопируйте его на телефон и установите (разрешите установку из неизвестных источников).

Либо подключите телефон по USB (включив «Отладку по USB») и нажмите кнопку Run в Android Studio.

## iPhone
```bash
npm install @capacitor/core @capacitor/cli @capacitor/ios
npx cap add ios
npx cap sync ios
npx cap open ios
```
В Xcode выберите свой Team в Signing & Capabilities и запустите на устройстве.

## Если меняете страницу
Правьте `www/index.html`, затем выполните `npx cap sync`.

## Иконка и название
- Название: `capacitor.config.json` → `appName`.
- Идентификатор `appId` (com.example.hourstracker) замените на свой, если будете публиковаться в магазинах.
- Иконку удобно сгенерировать через `@capacitor/assets` (положите `assets/icon.png` 1024×1024 и выполните `npx capacitor-assets generate`).

## Заметка о данных
Записи хранятся во встроенном браузере приложения (localStorage) и сохраняются между запусками.
Они удаляются при удалении приложения или очистке его данных. Для резервной копии
можно позже добавить экспорт в файл.
