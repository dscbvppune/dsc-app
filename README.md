<h1 align="center"><span><h3>DSC Web-App</h3></span>
<div align="center">
<a href="https://flutter.dev/">
<img src="https://img.shields.io/badge/Built with-flutter-blue?style=flat-square" alt="flutter"/>
</a>
<span>|</span>
<a href="https://github.com/dscbvppune/dsc/commits/master/">
<img src="https://img.shields.io/github/last-commit/dscbvppune/dsc?style=flat-square" alt="last commit"/>
</a>
<span>|</span>
<a href="https://github.com/dscbvppune/dsc/blob/master/LICENSE">
<img src="https://img.shields.io/badge/License-MIT-purple?style=flat-square" alt="license"/>
</a>
</div>
</h1>

<p align="center">
<img src="/docs/images/events.png" width="32%" alt="events"/>
<img src="/docs/images/home1.png" width="34%" alt="home"/>
<img src="/docs/images/coc.png" width="32%" alt="code of conduct"/>
</p>

## Overview

This project aims at making websites easier to manage. We at **DSC BVP Pune** noticed that many DSC's have outdated websites or do not even have an existing website. In order to solve this issue, we came up with a solution where maintainers could easily manage their websites using a mobile app.

## Features

| Feature                 | Description                                                                                |
| ----------------------- | ------------------------------------------------------------------------------------------ |
| **Built using Flutter** | The App is built exclusively in Flutter, while the adjoining website is built using Vue.js |
| **Portability**         | This Web-App can be used as a template by other Student Clubs                              |
| **User Experience**     | User-friendly and reliable, as well as handy and easy to use                               |
| **Powered by Firebase** | Cloud Firestore of Firebase provides solutions for storage issues                          |

## Getting Started

1. [Fork](https://github.com/dscbvppune/dsc/fork) our repository and clone it locally.
2. Open the repo in [VSCode](https://code.visualstudio.com/) or [Android Studio](https://developer.android.com/studio).
3. Open [Firebase Console](https://console.firebase.google.com/) and create a new project.
4. Connect your mobile-app project, either Android or iOS, with Firebase.
5. For Android refer to Firebase docs: [Add Firebase to your Android project](https://firebase.google.com/docs/android/setup?authuser=0).
6. For iOS refer to the Firebase docs: [Add Firebase to your iOS project](https://firebase.google.com/docs/ios/setup?authuser=0).
7. After setup has been done, Connect your phone to PC or MAC via USB.
8. Build the application in the IDE which you use for Flutter development or run `flutter run --release` on your console.
9. For setting up Firestore refer to the documentation below.
10. Great! Now your app is ready to go.
11. Enter the gmail ID of your DSC(admin) account that will have create, delete and update rights.
12. Add details of your team members, events organized by your DSC and the Code of Conduct of your DSC.
13. For Android users: If you want to build the apk: Run `flutter build apk --release` in your console.
14. For iOS users : Run 'flutter build ios' in your console of Xcode. Refer [Create a build archive](https://flutter.dev/docs/deployment/ios#create-a-build-archive) for detailed info.

### Setting up on Firestore

#### Setting security rules on Firestore
Create a Firestore Database in production mode, and add the following security rules to the database, to add authentication for only specific people to be able to update details on Firestore:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read;
      allow create, write, update, delete: if request.auth.token.email.matches("dscchapteremailaddress[@]gmail[.]com");
    }
  }
}
```

#### Setting security rules on Firebase Storage
Enable the Firebase Storage, and add the following security rules to the database, to add authentication for only specific people to be able to add / update media to the storage bucket:
```
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read;
      allow write, create, delete, update: if request.auth.token.email.matches("dscchapteremailaddress[@]gmail[.]com");
    }
  }
}
```

## Technology Stacks

#### Frontend Stacks

- Flutter

#### Backend Stacks

- Firebase

## Directory Structure

```
dsc
├── android
│    └── *
├── assets
│   └── fonts
│       └── *
│   └── icons
│       └── *
│   └── images
│       └── *
│   └── logos
│       └── *
│   └── svg
│       └── *
├── docs
│   └── images
│       └── *
├── ios
│   └── *
├── lib
│   ├── pages
│   │   ├── achievementsPage.dart
│   │   ├── addEvent.dart
│   │   ├── addGuidelines.dart
│   │   ├── addMember.dart
│   │   ├── cocPage.dart
│   │   ├── editHomePage.dart
│   │   ├── eventDescription.dart
│   │   ├── eventsPage.dart
│   │   ├── homePage.dart
│   │   ├── loginPage.dart
│   │   ├── manageCOC.dart
│   │   ├── memberDetails.dart
│   │   ├── splashPage.dart
│   │   └── teamPage.dart
│   ├── services
│   │   ├── authHandler.dart
│   │   ├── authService.dart
│   │   ├── buttonBuilder.dart
│   │   └── pageHandler.dart
│   └── main.dart
└── test
    └── *
```

#### Function of each file

| File                                                      | Function                                                |
| --------------------------------------------------------- | ------------------------------------------------------- |
| [achievementsPage.dart](/lib/pages/achievementsPage.dart) | Displaying achievements of DSC (WIP)                    |
| [addEvent.dart](/lib/pages/addGuidelines.dart)            | Page for adding events                                  |
| [addGuidelines.dart](/lib/pages/addGuidelines.dart)       | Page for adding guidelines for your DSC                 |
| [addMember.dart](/lib/pages/addMember.dart)               | Page for adding team members of your DSC                |
| [cocPage.dart](/lib/pages/cocPage.dart)                   | Code of Conduct page of your DSC                        |
| [editHomePage.dart](/lib/pages/editHomePage.dart)         | Page for editing homepage of your DSC's website         |
| [eventDescription.dart](/lib/pages/eventDescription.dart) | Description page for events                             |
| [eventsPage.dart](/lib/pages/eventsPage.dart)             | Pages for displaying all events of your DSC             |
| [homePage.dart](/lib/pages/homePage.dart)                 | Home page of the app                                    |
| [loginPage.dart](/lib/pages/loginPage.dart)               | Login page of the app for signing-in with google        |
| [manageCOC.dart](/lib/pages/manageCOC.dart)               | Page for altering code of conduct of your DSC           |
| [memberDetails.dart](/lib/pages/memberDetails.dart)       | Adding details of your team                             |
| [splashPage.dart](/lib/pages/splashPage.dart)             | Temporary loading page with circular progress indicator |
| [teamPage.dart](/lib/pages/teamPage.dart)                 | Page for displaying your DSC                            |
| [authHandler.dart](/lib/services/authHandler.dart)        | Dart file for user auth detection                       |
| [authService.dart](/lib/services/authService.dart)        | Dart file for google and firebase login                 |
| [buttonBuilder.dart](/lib/services/buttonBuilder.dart)    | Dart file for building stretchable raised buttons       |
| [pageHandler.dart](/lib/services/pageHandler.dart)        | Dart file for handling navigation of pages              |
| [main.dart](/lib/main.dart)                               | Entry point of the material app that calls authHandler  |

## Contributors

| Name              | Nickname                                          | E-Mail                                                                |
| ----------------- | ------------------------------------------------- | --------------------------------------------------------------------- |
| Abhishek Dubey    | [Abhi011999](https://github.com/Abhi011999)       | [abhi.dubey011999@gmail.com](mailto:abhi.dubey011999@gmail.com)       |
| Nishchay Verma    | [Nishchayverma](https://github.com/Nishchayverma) | [nishchayverma20@gmail.com](mailto:nishchayverma20@gmail.com)         |
| Priyanshu Agarwal | [priyanshu-01](https://github.com/priyanshu-01)   | [priyanshu.agarwal88@gmail.com](mailto:priyanshu.agarwal88@gmail.com) |
| Sparsh Tandon     | [codesparsh](https://github.com/codesparsh)       | [snowmansparsh4@gmail.com](mailto:snowmansparsh4@gmail.com)           |

## Contributing

See [CONTRIBUTING.md](/CONTRIBUTING.md)

## Support

- If you have any issues, feel free to hit us up at [dscbvppune@gmail.com](mailto:dscbvppune@gmail.com).
- You can also put up queries on GitHub issues [here](https://github.com/dscbvppune/dsc/issues).

## License

This project is licensed under the MIT License - see the [LICENSE](/LICENSE) file for details.
