# `react-native-appvirality`

A React Native module to show system Image chooser. Currently only supports Android.

### Installation

```sh
npm i --save react-native-appvirality
```

### Add it to your android project

In `android/settings.gradle`

```gradle
...

include ':react-native-appvirality'
project(':react-native-appvirality').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-appvirality/android')
```

In `android/app/build.gradle`

```gradle
...

dependencies {
    ...

    compile project(':react-native-appvirality')
}
```

Register module (in `MainActivity.java`)

```java
import android.content.Intent;  // <--- import
import io.scrollback.AppviralityPackage;  // <--- import

public class MainActivity extends Activity implements DefaultHardwareBackBtnHandler {
  ......

  private AppviralityPackage mChoosersPackage = new AppviralityPackage(this); // <------ create new instance

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    mReactRootView = new ReactRootView(this);

    mReactInstanceManager = ReactInstanceManager.builder()
      .setApplication(getApplication())
      .setBundleAssetName("index.android.bundle")
      .setJSMainModuleName("index.android")
      .addPackage(new MainReactPackage())
      .addPackage(new AppviralityPackage(this)) // <------ add the package
      .setUseDeveloperSupport(BuildConfig.DEBUG)
      .setInitialLifecycleState(LifecycleState.RESUMED)
      .build();

    mReactRootView.startReactApplication(mReactInstanceManager, "ExampleApp", null);

    setContentView(mReactRootView);
  }

  ......

}
```

## Usage

First import the module as follows:

```js
import React from "react-native";

const {
  NativeModules: {
    AppviralityModule
  }
} = React;
```
