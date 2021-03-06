### Step 1

`yarn add @notifee/react-native`

### Step 2

Open `apps/mobile/android/build.gradle`

Add

```
maven {
    url "$rootDir/../node_modules/@notifee/react-native/android/libs"
}
```


### Step 3

Open `apps/mobile/android/app/src/main/AndroidManifest.xml`

Add `android:exported="true"`

```
    <activity
      android:name=".MainActivity"
      android:label="@string/app_name"
      android:configChanges="keyboard|keyboardHidden|orientation|screenSize|uiMode"
      android:launchMode="singleTask"
      android:windowSoftInputMode="adjustResize"
      android:theme="@style/Theme.App.SplashScreen"
      android:exported="true"
    >
```


### Step 4

iOS needs permissions

```
async function checkApplicationPermission() {
  const settings = await notifee.requestPermission();

  // settings only available on iOS
  if (settings) {
    if (settings.authorizationStatus) {
      console.log('User has notification permissions enabled');
    } else {
      console.log('User has notification permissions disabled');
    }
  }
}
```


### Step 5: Install @react-native-firebase/app

- Create firebase project
- `yarn add @react-native-firebase/app`
- Follow https://rnfirebase.io/#3-ios-setup
- Manual linking: https://rnfirebase.io/install-ios
- Manual linking: https://rnfirebase.io/install-android
- https://jmp.sh/lhQKlyo

### Step 6: Install @react-native-firebase/messaging

- https://rnfirebase.io/messaging/usage/installation/android
- https://rnfirebase.io/messaging/usage/installation/ios




---

https://github.com/invertase/react-native-notifee/issues/256#issuecomment-787754998
