# Android — How to add Gradle dependencies using ‘foreach’

A big project in Android with several modules also has several Gradle files that need to be configured, and that´s a tedious task. Something that is usually done is adding dependencies to each module, in this project it will be explained how to control all modules dependencies using just a single Gradle file.

The code inside [this repository is explained here][1]

## From

```
dependencies {

  compile ‘com.android.support:appcompat-v7:24.2.0’

  compile ‘com.google.dagger:dagger:2.7’
  apt ‘com.google.dagger:dagger-compile:2.7’
  compile ‘io.reactivex:rxjava:1.2.0’
  compile ‘io.reactivex:rxandroid:1.2.1’
  compile ‘com.squareup.okhttp3:okhttp:3.4.1’
  compile ‘com.google.code.gson:gson:2.7’

  testCompile ‘junit:junit:4.12’

}
```

## To

```groovy

  dependencies {
      rootProject.appModuleDependencies.each {
          add(it.configuration, it.dependency, it.options)
      }
  }

```


License
-------

    Copyright 2016 Fabio Santana (fabiomsr)

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
    
[1]:https://medium.com/@develodroid/android-how-to-add-gradle-dependencies-using-foreach-c4cbcc070458#.2588yruk5
