---
title: Add Flutter to existing app
description: Adding Flutter as a library to an existing Android or iOS app.
---

## Add-to-app

It's sometimes not practical to rewrite your entire application in Flutter all
at once. For those situations, Flutter can be integrated into your existing
application piecemeal, as a library or module.
That module can then be imported into your Android or iOS
(currently supported platforms) app to render a part of your
app's UI in Flutter. Or, just to run shared Dart logic.

In a few steps, you can bring the productivity and the expressiveness of
Flutter into your own app.

As of Flutter v1.12, add-to-app is supported for the basic scenario of
integrating one full-screen Flutter instance at a time per app.
It currently has the _**following limitations**_:

* Running multiple Flutter instances or running in partial screen
  views may have undefined behavior.
* Using Flutter in background mode is still a WIP.
* Packing a Flutter library into another sharable library
  or packing multiple Flutter libraries into an application isn't supported.
* Plugins used in add-to-app on Android should undergo [flutter.dev/go/android-plugin-migration](https://flutter.dev/go/android-plugin-migration)
  and use the [FlutterPlugin](https://api.flutter.dev/javadoc/io/flutter/embedding/engine/plugins/FlutterPlugin.html)-based
  APIs. Plugins that don't support FlutterPlugin may have unexpected behaviors
  if they make assumptions that are untenable in add-to-app (such as assuming
  that a Flutter Activity is always present).

## Supported features

### Add to Android applications

{% include app-figure.md image="development/add-to-app/android-overview.gif" alt="Add-to-app steps on Android" %}

* Auto-build and import the Flutter module by adding a Flutter SDK hook to
  your Gradle script.
* Build your Flutter module into a generic
  [Android Archive (AAR)][] for integration into your
  own build system and for better Jetifier interoperability
  with AndroidX.
* [`FlutterEngine`][java-engine] API for starting and persisting
  your Flutter environment independently of attaching a
  [`FlutterActivity`][]/[`FlutterFragment`][] etc.
* Android Studio Android/Flutter co-editing and module
  creation/import wizard.
* Java and Kotlin host apps are supported.
* Flutter modules can use [Flutter plugins][] to interact
  with the platform. Android plugins should be
  [migrated to the V2 plugins APIs][]
  for best add-to-app correctness. As of Flutter v1.12,
  most of the plugins [maintained by the Flutter team][]
  as well as [FlutterFire][] have been migrated.
* Support for Flutter debugging and stateful hot reload by
  using `flutter attach` from IDEs or the command line to
  connect to an app that contains Flutter.

### Add to iOS applications

{% include app-figure.md image="development/add-to-app/ios-overview.gif" alt="Add-to-app steps on iOS" %}

* Auto-build and import the Flutter module by adding a Flutter
  SDK hook to your CocoaPods and to your Xcode build phase.
* Build your Flutter module into a generic [iOS Framework][]
  for integration into your own build system.
* [`FlutterEngine`][ios-engine] API for starting and persisting
  your Flutter environment independently of attaching a
  [`FlutterViewController`][].
* Objective-C and Swift host apps supported.
* Flutter modules can use [Flutter plugins][] to interact
  with the platform.
* Support for Flutter debugging and stateful hot reload by
  using `flutter attach` from IDEs or the command line to
  connect to an app that contains  Flutter.

See our [add-to-app GitHub Samples repository][]
for sample projects in Android and iOS that import
a Flutter module for UI.

## Get started

To get started, see our project integration guide for

<div class="card-deck mb-8">
  <a class="card" href="/docs/development/add-to-app/android/project-setup">
    <div class="card-body">
      <header class="card-title text-center m-0">
        Android
      </header>
    </div>
  </a>
  <a class="card" href="/docs/development/add-to-app/ios/project-setup">
    <div class="card-body">
      <header class="card-title text-center m-0">
        iOS
      </header>
    </div>
  </a>
</div>

## API usage

After Flutter is integrated into your project,
see our API usage guides for

<div class="card-deck mb-8">
  <a class="card" href="/docs/development/add-to-app/android/add-flutter-screen">
    <div class="card-body">
      <header class="card-title text-center m-0">
        Android
      </header>
    </div>
  </a>
  <a class="card" href="/docs/development/add-to-app/ios/add-flutter-screen">
    <div class="card-body">
      <header class="card-title text-center m-0">
        iOS
      </header>
    </div>
  </a>
</div>


[add-to-app GitHub Samples repository]: {{site.github}}/flutter/samples/tree/master/add_to_app
[Android Archive (AAR)]: https://developer.android.com/studio/projects/android-library
[Flutter plugins]: {{site.pub}}/flutter
[Flutter plugins]: {{site.pub}}/pub.dev/flutter
[`FlutterActivity`]: {{site.api}}/javadoc/io/flutter/embedding/android/FlutterActivity.html
[java-engine]: {{site.api}}/javadoc/io/flutter/embedding/engine/FlutterEngine.html
[ios-engine]: {{site.api}}/objcdoc/Classes/FlutterEngine.html
[FlutterFire]: {{site.github}}/FirebaseExtended/flutterfire/tree/master/packages
[`FlutterFragment`]: {{site.api}}/javadoc/io/flutter/embedding/android/FlutterFragment.html
[`FlutterViewController`]: {{site.api}}/objcdoc/Classes/FlutterViewController.html
[iOS Framework]: https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPFrameworks/Concepts/WhatAreFrameworks.html
[maintained by the Flutter team]: {{site.github}}/flutter/plugins/tree/master/packages
[migrated to the V2 plugins APIs]: /docs/development/packages-and-plugins/plugin-api-migration
