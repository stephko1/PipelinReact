fastlane documentation
================
# Installation

Make sure you have the latest version of the Xcode command line tools installed:

```
xcode-select --install
```

Install _fastlane_ using
```
[sudo] gem install fastlane -NV
```
or alternatively using `brew install fastlane`

# Available Actions
## Android
### android build
```
fastlane android build
```
Build and Sign the Android App
### android unit_test
```
fastlane android unit_test
```
Unit Tests
### android internal
```
fastlane android internal
```
Deploy to Internal
### android alpha
```
fastlane android alpha
```
Deploy to Alpha
### android ui_test
```
fastlane android ui_test
```
UI Testing
### android beta
```
fastlane android beta
```
Deploy to Beta
### android store
```
fastlane android store
```
Deploy to Store

----

This README.md is auto-generated and will be re-generated every time [fastlane](https://fastlane.tools) is run.
More information about fastlane can be found on [fastlane.tools](https://fastlane.tools).
The documentation of fastlane can be found on [docs.fastlane.tools](https://docs.fastlane.tools).
