[![Maven Central](http://img.shields.io/maven-central/v/de.halfbit/edge-to-edge.svg)](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22de.halfbit%22%20a%3A%22edge-to-edge%22)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0)

# 🌖 Edge-to-Edge 
In meanwhile, here is an Android library for enabling [edge-to-edge content](https://developer.android.com/guide/navigation/gesturenav) and insetting views using simple Kotlin DSL.

# Getting Started

1. Configure transparent colors of the status and navigation bars in `res/values/styles.xml` by extending a theme without the action bar like `Theme.MaterialComponents.Light.NoActionBar` or `Theme.Design.Light.NoActionBar` or similar.

```xml
<resources>
    <style name="AppTheme" parent="Theme.MaterialComponents.Light.NoActionBar">
        ...
        <item name="android:windowDrawsSystemBarBackgrounds">true</item>
        <item name="android:windowTranslucentStatus">false</item>
        <item name="android:windowTranslucentNavigation">false</item>
        <item name="android:statusBarColor">@color/statusBar</item>
        <item name="android:navigationBarColor">@color/navigationBar</item>
    </style>
    
    <color name="statusBar">@android:color/transparent</color>
    <color name="navigationBar">@android:color/transparent</color>
</resources>
```

2. Remove `android:fitSystemWindows` attribute everywhere from layouts, if present.
3. Fit top and bottom views of each fragment as required.

```kotlin
override fun onViewCreated(view: View, savedInstanceState: Bundle?) {
    super.onViewCreated(view, savedInstanceState)
    edgeToEdge {
        appbar.fit { Edge.Left + Edge.Top + Right }
        recycler.fit { Edge.Bottom }
    }
    ...
}
```

See sample app for more edge-to-edge examples.

# Download
```gradle
repositories {
    mavenCentral()
}
dependencies {
    implementation 'de.halfbit:edge-to-edge:<version>'
}

```

# License
```
Copyright 2020 Sergej Shafarenka, www.halfbit.de

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
