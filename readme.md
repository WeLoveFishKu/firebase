## Config Firebase to App
#### 1. Register app
    
![Cuplikan layar 2023-05-21 193815](https://github.com/WeLoveFishKu/firebase/assets/44109243/64238b3e-6878-4b39-b416-67a573c30e76)


#### 2. Move google-services.json file into your module (app-level) root directory.

![android_studio_project_panel@2x](https://github.com/WeLoveFishKu/firebase/assets/44109243/18beecfe-9b3e-4270-b915-88ce6455c842)

#### 3. Add Firebase SDK
    - Add the plugin as a buildscript dependency to your project-level build.gradle file:
    - Root-level (project-level) Gradle file (<project>/build.gradle):

  ```sh
    buildscript {
      repositories {
        // Make sure that you have the following two repositories
        google()  // Google's Maven repository

        mavenCentral()  // Maven Central repository

      }
      dependencies {
        ...
        // Add the dependency for the Google services Gradle plugin
        classpath 'com.google.gms:google-services:4.3.15'

      }
    }

    allprojects {
      ...
         repositories {
           // Make sure that you have the following two repositories
           google()  // Google's Maven repository

           mavenCentral()  // Maven Central repository

         }
    }
```


 - Then, in your module (app-level) build.gradle file,  add both the google-services plugin and any Firebase SDKs that you want to use in your app:
  - Module (app-level) Gradle file (<project>/<app-module>/build.gradle): 
 
```sh
plugins {
  id 'com.android.application'

  // Add the Google services Gradle plugin
  id 'com.google.gms.google-services'

  ...
}

dependencies {
  // Import the Firebase BoM
  implementation platform('com.google.firebase:firebase-bom:32.0.0')


  // TODO: Add the dependencies for Firebase products you want to use
  // When using the BoM, don't specify versions in Firebase dependencies
  implementation 'com.google.firebase:firebase-analytics-ktx'


  // Add the dependencies for any other desired Firebase products
  // https://firebase.google.com/docs/android/setup#available-libraries
}
```
