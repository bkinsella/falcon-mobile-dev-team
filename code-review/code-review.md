# Code Review for Mobile Applications

Mobile technologies have enabled companies of all sizes to provide new and useful services to their customers, increase brand equity, enhance customer experience, and gain valuable insight into their customers by providing aggregated usage metrics and analytics. Unfortunately, poor deployment of mobile technologies can have the opposite effect: disgruntled users, poor brand appreciation, and absent or confusing metrics and analytics. It is critical that the deployed mobile technologies are intuitive, secure, and stable.

The purpose of the Certification Template is to give both the application development team and
certification team a template for the code certification process. This template is a guide only
and sections can be added / removed based on the application that is being reviewed. It is helpful
for application development teams to review the template before certification to understand the
parts of the project that will be reviewed, and possibly correct any issues before the certification
starts.

Certifications are setup to ensure that all mobile applications follow similar quality standards so
that we can provide a consistent portfolio for members and our teammates.

#### TABLE OF CONTENTS

 * [Code Review Process](#code-review-process)
 * [Phase One: High-level overview](#phase-one-high-level-overview)
 * [Phase Two: Deeper Dive](#phase-two-deeper-dive)
 * [Phase Three: Platform Deployment Analysis](#phase-three-platform-deployment-analysis)
 * [Certification Outputs](#certification-outputs)

## Code Review Process

The code review process begins by identifying various code-quality elements relating to the mobile technologies in question, and then proceeds with the evaluation. By supplying underlying metrics and noting whether or not the identified code-quality elements are present, the code review process remains as objective as possible while delivering real, actionable results.

## Phase One: High-level overview

In this track, our team will gain a sense for the overall health of your mobile application(s). A senior software engineer  will guide this phase, leading the collective team through analysis and prioritization activities  which will drive the subsequent analysis phases.

#### CODE REPOSITORY
Frequent commits tend to illustrate a dynamic code base where features are implemented in consumable bites. Longer gaps between code commits tend to illustrate complex pieces of code that may carry bigger application risks. Our team will assess the current code repository tool used and the underlying check-in/ commit frequency of the development team.

References:

- [Branching Strategy](/branching-strategy/branching_strategy.md)

#### APP NAME
Applications should be named so that the name is clearly visible when loaded on a users device. Ideal names are short and have no truncation or abbreviation.

- Does the name have a good length for display on all target devices?
- Is the name appropriate?
- Is the name unique?

#### APP ID
Applications should have an appropriate app ID. This should be in the form of _com.[company_name].[app_name]_ for iOS. On Android, the package and application name should correlate to each other and begin with _com.[company_name]_ App IDs are permanent in the AppStore, so care should be taken to ensure the ID is accurate and appropriate. The _company_name_ could also be the name of the SBI instead of DaVita.

- Is the App ID set?
- Is the App ID appropriate and fall within the _com.[company_name].*_ domain?
- Is the App ID unique to this application?
- Is the production signing certificate backed up in a secure place?

#### APP VERSION
Applications should follow the semantic version scheme. See the 'App Version Guide' for a detailed set of instructions.

- Is the App Version set (both version name and version code)?
- Is the App Version appropriate for this release?
- For iOS are both the marketing and project version numbers set and accurate?

References:

- [Version Number Guide](/version-number-guide/version_number_guide.md)

#### APP BINARY
Application binaries should be kept as small as possible. Ideally app binaries should include the name of the application
plus the version number. This ensures that the correct binary is loaded to the AppStore or on a device.

- Does the binary follow a naming convention that includes the version number?
- How large is the binary?
- Can the application be loaded over the cell network (< 100MB for iOS), or does it require a wifi connection?
- How large is the Application Binary (.app/app_name)? (For iOS it can be no larger than 60MB, for Android 50MB).


#### APPLICATION BUILD AND STATIC ANALYSIS
All projects should build cleanly without warnings and errors. Source code may have subtle errors that slip by the compiler and manifest themselves only at runtime. These bugs are much harder to identify and fix. The Xcode IDE and Android SDK Tools include static analyzers that find flaws and potential bugs in the source code of a project.

- How many warnings are generated from the compile?
- How many warnings are generated from the static analyzer?
- How many issues are reported from the Fortify scan?

#### CONTINUOUS INTEGRATION
Projects that maintain a frequent automated build process have a higher level of quality and maintainability. An automated build should be performed regularly (on every push to the source code repository is ideal) and the results of the build made available to the development and QA teams. Automated system can also optionally include testing and security/code scans.

- Does the project team maintain a build server?
- What is the frequency of automated builds?
- Are the results of the automated build reported to the team? How?
- Are automated unit tests performed during the build process?
- Are any additional scans performed during the build process? If so, which ones?

#### OS VERSION SUPPORT
Application builds will be tested for all of the supported iOS and/or Android operating systems and validated for backward capability (if applicable). For public iOS applications, the App Store has some special considerations:

_You can't upload two different versions of your application that support different versions of the OS. Once you drop support for an OS, the user will stop seeing updates for their application, but you can direct users to an older upload that will work for their version._

- What is the minimum version that the application will run on?
- Will the application run on the latest version of the OS?
- Will this update of the application cause users of the old version to be abandoned?
- Does the application perform any checks to ensure that it only runs on supported OS versions?
- Is there a forced upgrade in place for outdated OS?

#### DEVICE SUPPORT
Applications should support the widest number of devices possible, but may target specific subsets if that makes sense for the application (an iPad only application for example). Applications should implement fallbacks for running on unsupported devices since in some cases it is difficult to restrict apps to specific devices in the public app stores. For applications that can run on devices with different screen sizes, they should support each size in the most optimal way (for retina displays, for example, the app should include both low-res and high-res version of their images). On Android it's important to decide which densities of images to supply and which ones can be scaled by the system.

- Does the application display correctly on all supported screen resolutions?
- Does the application support allowed screen orientations (portrait/landscape)?
- Does the application require any device specific features (camera/compass/etc)?

#### USER PERMISSIONS
In iOS, some platform features require the user to explicitly grant permission before they can be used (e.g. location services). This is handled automatically by the OS in most cases, but should be handled well by the application. Ideally the application should only ask for permission
for required features, and only before that feature is used. Also the user should be told why
the permission is required and the consequences of granting or not granting it. On Android, a user will be presented the list of permissions an app requires before installing it, so the number of permissions should be kept as small as possible. Ideally, the app description in Google Play would contain a justification of each permission needed by the app.

- Which system capabilities does the application use?
- Does the application properly ask the user for this permission (iOS only)?

#### DEVELOPMENT ENVIRONMENT
Choosing the correct development tools is a key factor for a successful project. Using standard tools allows teams to work together more easily. Also the latest development tools are usually important for supporting the most recent mobile operating systems and hardware.

- Which development tools are being used?
- What versions of the development tools are required?

References:

- [iOS Best Practices](/coding-standards/ios-best-practices.md)
- [Android Best Practices](/coding-standards/android-best-practices.md)

#### PROJECT STRUCTURE
The larger the project is, the more important it becomes to impose a reasonable structure, in order to assist in long-term maintenance and sustainability. Project structures should follow current best practices for each platform.

- Is the code following recommended standards?
- If not following a recommended approach, is it consistent to its own approach?

References:

- [iOS Best Practices](/coding-standards/ios-best-practices.md)
- [Android Best Practices](/coding-standards/android-best-practices.md)

#### UNIT TEST ANALYSIS
Unit tests should be written to cover non-UI aspects of an application such as: Network requests, model layer interactions and helper/utility classes. It is recommended to use the built-in unit test frameworks from Apple & Google because they provide good functionality and require no additional 3rd party dependencies.

References:

- [Testing with Xcode](https://developer.apple.com/library/ios/documentation/DeveloperTools/Conceptual/testing_with_xcode/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014132)

## PHASE TWO: Deeper Dive

In this phase, mobile apps are examined more closely. Every source code file will be observed to establish common patterns across the application.

#### DEFINITION OF ARCHITECTURAL PATTERNS
Before diving into the code, determine the common architectural patterns being used (e.g., Model-View-Controller). This will not only provide a roadmap for the Phase Two code analysis, but also help provide implementation-specific suggestions moving forward.

References:

- [iOS Best Practices](/coding-standards/ios-best-practices.md)
- [Android Best Practices](/coding-standards/android-best-practices.md)


#### SYNTAX RELEVANCY
Compare how the code base leverages the latest features and capabilities from the newest available mobile platforms. Syntax relevancy is often a good way to determine how up-to-speed the current development staff is on emerging technologies.

References:

- [ObjectiveC Zen Book](https://github.com/objc-zen/objc-zen-book)

#### NAMING CONVENTIONS
Good class/object/variable naming conventions aren’t necessarily indicative of healthy or unhealthy code, but it does indicate a self-documenting and cohesive development strategy. If standard naming conventions are followed, it’s indicative of a shared code base amongst a group of developers as opposed to a set of disparate units of code written by individual entities.

References:

- [ObjectiveC Zen Book](https://github.com/objc-zen/objc-zen-book)
- [Android Code Style](https://source.android.com/source/code-style.html)

#### CODING STYLE
Quality code is important to the long term maintenance of an application. The MCOE code style reference should be used as a guide to judge the coding style.

- Does the code follow industry standards?
- If the code is following its own style, is it consistent within itself?
- Is all code formatted identically?

References:

- [ObjectiveC Zen Book](https://github.com/objc-zen/objc-zen-book)
- [Android Code Style](https://source.android.com/source/code-style.html)

#### MEMORY MANAGEMENT
Application memory management is the process of allocating memory during your program’s runtime, using it, and freeing it when you are done with it. Compare the application's memory management with established best practices for mobile platforms.

References:

- [Apple Memory Management Guide](https://developer.apple.com/library/ios/documentation/General/Conceptual/DevPedia-CocoaCore/MemoryManagement.html)
- [Android Developer Guide](https://developer.android.com/training/articles/memory.html)

#### EXCEPTION HANDLING
Good exception and error handling is an indication of an application’s health because it shows awareness of issues that may arise in a runtime environment and how to gracefully react to them if they should occur. Exceptions should be handled consistently throughout the codebase.

References:

- [Apple Exception Handling](https://developer.apple.com/library/ios/documentation/General/Conceptual/DevPedia-CocoaCore/ExceptionHandling.html#//apple_ref/doc/uid/TP40008195-CH18-SW1)
- [Android Exception Handling](https://source.android.com/source/code-style.html)

#### SYSTEM ENVIRONMENTS
Applications should manage system environments correctly between different builds of an application. Production code should NOT include references to the QA or development environments in any way, including credentials, mock data, and test cases. Ideally this should be precompiler/scheme setting that doesn't get included in the production compile.
If the app supports more than one non-production environment, an environment switchter must be included in the UI. This will allow for faster testing and also ensure that endpoints aren't hard-coded. This environment switcher must be excluded from the production build.

- How does the application handle different backend environments?
- Are any mock data or test user IDs included in the production build?
- Does the UI include an environment switcher?

#### CONSOLE LOGGING
Applications should never write to the console log (or any other file based log) in their production version. Writing to logs is acceptable in debug/test/QA builds. Writing to logs in a production build is a security risk and also can be a performance issue.

- Does the application log anything to the console when running the production version?

References:

- [iOS Best Practices](/coding-standards/ios-best-practices.md)
- [Android Developer Guide](https://source.android.com/source/code-style.html)

#### CODE SIZE/RESPONSIBILITY
Oversized methods are hard to maintain long-term and are an indication of code that is doing too much (making them harder to unit test and diagnose). Core classes, methods, and architectural layers should be sized manageably.

References:

- [iOS Best Practices](/coding-standards/ios-best-practices.md)
- [Android Best Practices](/coding-standards/android-best-practices.md)


#### MODEL LAYER CONSTRUCTION
The model layer is responsible for encapsulation/persistence of application data. If the app is using Core Data (iOS) or SQLite (Android), ensure that the data model is sufficiently normalized and sensible.

References:

- [iOS Best Practices](/coding-standards/ios-best-practices.md)
- [Android Best Practices](/coding-standards/android-best-practices.md)


#### THREADING
Determine if multi-threading is leveraged in the application. Specifically, is all application activity managed on one thread or is some activity (e.g., the Core Data stack in iOS) set up on a background thread for concurrent processing. Are AsyncTasks with ThreadPoolExecutors used on Android? Improper threading can lead to memory leaks and race conditions in an application, which are typically very difficult to diagnose and fix.

References:

- [ObjectiveC Zen Book](https://github.com/objc-zen/objc-zen-book)
- [Android Developer Guide](https://developer.android.com/guide/components/processes-and-threads.html)

#### SECURITY
Security is important for all Applications. [Sensitive Information](#appendix) must be protected while being transmitted over the internet/network and if stored locally on the device. All secure data must use HTTPS and proper SSL protections. Any sensitive data stored on the device must also be encrypted and stored in a secure file system or database. If the application will be used by different users on the same device (device sharing) then all sensitive patient data must be cleared when a user logs out of the application.  
Certain apps may cache network requests if there is no network connectivity and submit them at a later time when connectivity has been restored. In this case, the cached requests must be encrypted at rest and also be deleted if a different user logs into the app. This scenario is likely in a clinical setting. Applications should also prevent sensitive data from being included in a users backup.  
"Kill Switch" is a feature that lets the login server signal the app that all local data must be deleted. This is implemented via an HTTP 419 status code when a user tries to log in. Also, in case of an HTTP 419 status code, the user is not allowed to log into the app.

Also, the application should be run through the [Security Testing process](/security-testing/security-testing.md).

The **minimum sercurity requirements** for an app are:

- If the app makes network requests that include sensitive data it has to utilize HTTPS and SSL protections
- Any local, sensitive data must be encrypted and stored in a secure location
- Any locally cached network requests need to be encrypted and deleted if a different user signs in
- Sensitive files have to be marked to ensure they will not be included in a backup
- The app must implement "kill switch" functionality, which will delete any local data
- Any screen shots are to be blurred in the task manager (see Android and iOS best practices)
- Data cannot be stored on an external SD card
- The app must have an adequate timeout protection enforced by the backend components (20 minutes for apps handling sensitive information)

For more detailed information on app security see

- [iOS Best Practices](/coding-standards/ios-best-practices.md#security)
- [Android Best Practices](/coding-standards/android-best-practices.md#security)

#### THIRD-PARTY LIBRARIES
Nearly all applications will leverage code from other projects. It is important to ensure that this code is included in a consistent manner and that the projects used have been reviewed and approved.

For 3rd party libraries, the proper attribution must be made in order to include the library in an application. Each license should be examined to determine if an attribution must be made. In general there are two types of requirements that should be followed:

  1. The original source code attribution should not be modified and should be included. Also, if required, a LICENSE file should be included in the application bundle/package.
  2. Attributions should be made in an applications about screen. This can be included in the application itself, or in the settings of the application (iOS).

- What third-party code libraries are used in the application?
- How are libraries included in the project?
- Is the correct license attribution made for 3rd party code libraries that require it?
- Is any 3rd party code being used against the terms of its license?

References:

- [iOS Best Practices](/coding-standards/ios-best-practices.md)
- [Android Best Practices](/coding-standards/android-best-practices.md)


#### LOCALIZATION / INTERNATIONALIZATION
For applications that have a broad audience, particularly customer-facing applications, localization support should be enabled for non-English speaking individuals.

References:

- [Apple Localization Guide](https://developer.apple.com/internationalization/)
- [Android Localization Guide](http://developer.android.com/guide/topics/resources/localization.html)


## Phase Three: Platform Deployment Analysis
In this phase, determine the applications’ readiness for the Apple App Store or the Google Play store. Due to the highly visual nature of this analysis, leveraging specialized UX resources is recommended. This phase includes the following activities:

#### TEST FOR MEMORY LEAKS
Memory leaks are blocks of allocated memory that the program no longer references. Leaks waste space by filling up pages  of memory with inaccessible data. In addition being an indication of bad coding patterns, if you are developing on the iOS platform, memory leaks will cause an application to be rejected by Apple.

#### HUMAN INTERFACE GUIDELINES
Compare the front-end components of the applications against Apple’s Human Interface Guidelines. These guidelines described visual patterns (e.g., hit target size, navigation paradigms) that should be followed across applications in the App Store. Similarly, failure to follow Apple’s guidelines can cause an application to be rejected during review.

## Certification outputs

#### CERTIFICATION REPORT

All the above phases will be documented to include the important findings from the reviewer in each section, as well as recommendations. The recommendations may include items that must be fixed before release, items that should be fixed in the next release, or items that should be fixed/considered for future releases.


## Appendix

_Sensitive Information_ is any information for which the loss, misuse, modification, or unauthorized access could adversely affect DaVita’s patients, employees, partners, vendors, compliance efforts, security, finances, reputation or other important DaVita interests.
(Examples of Sensitive Information include, but are not limited to, ePHI, PII, intellectual property, financial records, contracts, business agreements, attorney records and other information subject to non-disclosure arrangements).

---

![DaVita Mobile Community of Excellence Logo](images/MCOE_logo.png)

**Updated:** January 2015
