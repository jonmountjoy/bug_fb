# coma

A new Flutter project demonstrating a problem with Firebase.

try:

    flutter build ios --no-codesign

It should compile successfully.

```
Warning: Building for device with codesigning disabled. You will have to manually codesign before deploying to device.
Building com.example.coma for device (ios-release)...
Running pod install...                                             697ms
Running Xcode build...
 └─Compiling, linking and signing...                        992ms
Xcode build done.                                            2.8s
Built /private/tmp/coma/build/ios/iphoneos/Runner.app.
```

If you modify `ios/Podfile` and remove the `#` from this line:

```
# pod 'FirebaseFirestore', :git => 'https://github.com/invertase/firestore-ios-sdk-frameworks.git', :tag => '10.17.0'
```

Try and compile again: `flutter build ios --no-codesign`

It fails with:

```
Warning: Building for device with codesigning disabled. You will have to manually codesign before deploying to device.
Building com.example.coma for device (ios-release)...
Running pod install...                                           2,048ms
Running Xcode build...
 └─Compiling, linking and signing...                        708ms
Xcode build done.                                            3.5s
Failed to build iOS app
Error (Xcode): Undefined symbols:


Error (Xcode): Linker command failed with exit code 1 (use -v to see invocation)


Encountered error while building for device.
```

This used to work. It also retroactively fails on older codebases using an older link: `https://github.com/invertase/firestore-ios-sdk-frameworks.git`
