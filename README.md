# Flutter Template App
#### Need to update in CICD and Flavour files
###### Regarding CICD 
- create-keychain.sh
    - Add your app's certificate name and password
- build.sh
    - Add your app's profile file name
- .gitlab-ci.yml
    - Update app name (without space) and fvm version
- ExportOptions.plist
    - Update bundle id and profile actual name, not file name
###### Regarding Flavours
- Setup proper schema in xcode for all configuration
- Update manifeast file for android 
- Add configuration file in vscode 

#### Run and build command with flavors 
iOS flavors
flutter run --flavor development --target lib/main_dev.dart
flutter run --flavor staging --target lib/main_staging.dart
flutter run --flavor production --target lib/main_production.dart
flutter run --flavor enterprise --target lib/main_enterprise.dart

flutter build ipa --flavor development --target lib/main_dev.dart
flutter build ipa --flavor staging --target lib/main_staging.dart
flutter build ipa --flavor production --target lib/main_production.dart
flutter build ipa --flavor enterprise --target lib/main_enterprise.dart

Android flavors
flutter run --flavor development --target lib/main_dev.dart
flutter run --flavor staging --target lib/main_staging.dart
flutter run --flavor production --target lib/main_production.dart
flutter run --flavor enterprise --target lib/main_enterprise.dart

flutter build apk --flavor development --target lib/main_dev.dart
flutter build apk --flavor staging --target lib/main_staging.dart
flutter build apk --flavor production --target lib/main_production.dart
flutter build apk --flavor enterprise --target lib/main_enterprise.dart


## Requirements

- iOS 11+
- Xcode 13.2 +
- Android API 4.x +
- Android Studio 3.0 +
- Flutter 2.17.x


## Installation

#### yaml (Sampling)
You can use [Pubs](https://pub.dev/) to install `YourLibrary` by adding it to your `pubspec.yaml`:

```ruby
flutter:
    sdk: flutter

  flutter_localizations: # add this
    sdk: flutter

  # The following adds the Cupertino Icons font to your application.
  # Use with the CupertinoIcons class for iOS style icons.
  cupertino_icons: ^1.0.5
  
  # Effective Dart: Style Guide.
  # https://pub.dev/packages/lint
  # Compulsory
  flutter_lints: ^2.0.1

  # for bloc pattern
  # https://pub.dev/packages/rxdart
  # Optional
  rxdart: ^0.27.4

  # for localozation
  # https://pub.dev/packages/easy_localization
  # Compulsory
  easy_localization: ^3.0.1

  # Service locator
  # https://pub.dev/packages/get_it
  # Compulsory
  get_it: ^7.2.0

  # Shared Prefrence <=> User Default
  # https://pub.dev/packages/shared_preferences
  # Compulsory
  shared_preferences: ^2.0.15

  # Lottie for animation
  # https://pub.dev/packages/lottie
  # Optional
  lottie: ^1.3.0

  # For check internet connectivity
  # https://pub.dev/packages/connectivity
  # Optional
  connectivity_plus: ^2.3.2

  # For encrypt / decrypt
  # https://pub.dev/packages/encrypt
  # Optional
  encrypt: ^5.0.1

  # For device info
  # https://pub.dev/packages/device_info
  # Optional
  device_info: ^3.2.4

  # For flutter network calls
  # https://pub.dev/packages/dio/install
  # Optional if no network connectivity
  dio: ^4.0.6

 
```

#### Common classes

- Configuration 
- Constants
- Environment
- Extensions
- API Helper 
- Connectivity Helper 
- Haptic Helper 
- Shared Preference Helper
- Validation Helper
- Theme 
- Loader 
- Toast

#### Known Issues

- Loader Dismissed on press of physical back button

#### CICD Integration steps

* Create Profile folder
    1. Create Profile folder to root of project directory
    2. Add ios certificates files like .p12 & .mobileprovision
* Drag & drop create-keychain.sh to root of project directory
    1. Update # Development parameters at beginig of file
    2. Update CERTIFICATE_NAME with your certificate .p12 file(Note: please not include .p12 extension)
    3. Update KEY_PASSWORD with password of .p12 file
* Drag & drop .gitlab-ci.yml to root of project directory
    1. Update APP_NAME parameter with your project name
    2. Update client_email parameter with you client and PM email id using ',' seperated
* Drag & drop build.sh to root of project directory
    1. Update array parameters add your provisioning profile name to this array
* Drag & drop ExportOptions.plist file inside ios folder
    1. update bundle id with your ios project bundle id
    2. update profisioning profile name(Please Make sure of profisioning profile name not a File name.)
* GitLab repository side setup for CI/CD
    1. Enable runner: Git project setting -> CI/CD expand the Runner section -> Enable for available runner
    2. Environment variables: Git project setting -> CI/CD expand the environment variables section
    3. Add below parameters to git lab. Make sure name of parameters should be same as mention blow
        * DEVELOPER_EMAIL : developer email address
        * MMWEBHOOKURL : "https://chat.indianic.com/hooks/7sdmnjbd5iyk9b5qekxyo45rhr" (Fix for all project. it is flutter team bot url)
        * SENDOTA_TOKEN : “8f5ae02a-155f-420d-ac20-bc4b987c9e39” (Fixed for all projects)
    4. This are default parameters required for flutter CI/CD. you can check below reference link for more parameters



#### CICD Integration reference

* Flutter
    https://box.indianic.biz/index.php/s/LU8RxSCF6k47Rva
    Password: Flutter1234  
 * iOS
    > http://box.indianic.biz/index.php/s/brU6zABH219C89V/authenticate
    > Password: indianic
* Android
    **CI/CD**(https://docs.google.com/presentation/d/1mOMYmVSEH9w4SxexTCBy8epngfyXefFXP_K07a8GtL0/edit?usp=sharing)
    1. Enable runner: Git project setting -> CI/CD expand the Runner section -> Enable for available runner
    2. Environment variables: Git project setting -> CI/CD expand the environment variables section
        * ANDROID_SDK_PATH
        * DEBUG_BUILD_NAME
        * DEBUG_KEYSTORE_FILE
        * DEVELOPER_EMAILS
        * KEYSTORE_FILE
        * KEYSTORE_PASSWORD
        * PROJECT_NAME
        * KEY_ALIAS
        * KEY_PASSWORD
        * RELEASE_BUILD_NAME
        * SEND_OTA_TOKEN
        * URLOFMM
    3. Add script file into the project folder with file name ".gitlab-ci.yml" in Project Level
        (https://docs.google.com/document/d/1-w6sAI_eDcuHseXiKzE-huzEcYb0K0oHIyHJZWi5umY/edit?usp=sharing)



#### Git Tree 
```bash
.
├── README.md
├── analysis_options.yaml
├── android
├── assets
│   ├── fonts
│   ├── images
│   └── lottie    
├── build
│   └── ios    
├── flutter_base.iml
├── ios
│    └── ExportOptions.plist
├── lib
│   ├── main.dart
│   ├── reusable_component
│   │   ├── loader
│   │   └── toast    
│   ├── screens
│   │   ├── login
│   │   │   └── login.dart
│   └── utils
│       ├── common
│       │   ├── config.dart
│       │   ├── constants.dart
│       │   └── env.dart
│       ├── extensions
│       │   ├── align_extension.dart
│       │   ├── buildcontext_extension.dart
│       │   ├── double_extension.dart
│       │   ├── extension.dart
│       │   ├── list_extension.dart
│       │   ├── padding_extension.dart
│       │   ├── string_extension.dart
│       │   └── text_style_extension.dart
│       ├── helpers
│       │   ├── api_provider.dart
│       │   ├── connectivity.dart
│       │   ├── haptic_helper.dart
│       │   ├── shared_pref_helper.dart
│       │   └── validation_helper.dart
│       └── theme
│           ├── colors.dart
│           └── style.dart
├── Profile
├── .gitlab-ci.yml
├── build.sh
├── create-keychain.sh
├── pubspec.lock
├── pubspec.yaml
├── resources
│   └── langs
│       ├── ae.json
│       └── en.json
└── test
    └── widget_test.dart
```

## Contributer
- Flutter Team: 
Manish mundra, 
Nilesh Gurjar

## Project Detail
