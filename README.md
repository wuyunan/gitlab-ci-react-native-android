# gitlab-ci-react-native-android

## Android 26.0.2 and Fastlane 2.61.0

This Docker image contains react-native and the Android SDK and most common packages necessary for building Android apps in a CI tool like GitLab CI.

A `.gitlab-ci.yml` with caching of your project's dependencies would look like this:

```
image: wuyunan/gitlab-ci-react-native-android

stages:
- build

cache:
  key: ${CI_PROJECT_ID}
  paths:
  - android/.gradle/

build:
  stage: build
  script:
  - yarn
  - cd android && ./gradlew assembleDebug
  artifacts:
    paths:
    - android/app/build/outputs/apk/
```
