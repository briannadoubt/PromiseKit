# PromiseKit

Build `PromiseKit.xcframework` from the [origin repository](https://github.com/mxcl/PromiseKit).

- Add module file:

```
module PromiseKit {
    umbrella header "PromiseKit.h"
    export *
}
```

- Clone the PromiseKit project from here: https://github.com/mxcl/PromiseKit

- Checkout the version you want to build the framework, here we use v6:

- Run xcodebuild command to build the iOS libraries for simulator and real device:

```
xcodebuild archive \
 -scheme PromiseKit \
 -archivePath ~/Desktop/PromiseKit-iphonesimulator.xcarchive \
 -sdk iphonesimulator \
 SKIP_INSTALL=NO
```

```
xcodebuild archive \
 -scheme PromiseKit \
 -archivePath ~/Desktop/PromiseKit-iphoneos.xcarchive \
 -sdk iphoneos \
 SKIP_INSTALL=NO
```

- Run xcodebuild command to build the WatchOS framework for simulator and real device:

```
xcodebuild archive \
 -scheme PromiseKit \
 -archivePath ~/Desktop/PromiseKit-watchos.xcarchive \
 -sdk watchos \
 SKIP_INSTALL=NO
```

```
xcodebuild archive \
 -scheme PromiseKit \
 -archivePath ~/Desktop/PromiseKit-watchossimulator.xcarchive \
 -sdk watchsimulator \
 SKIP_INSTALL=NO
```

- Finally create the framework:

```
xcodebuild -create-xcframework \
    -framework "archives/PromiseKit-iphoneos.xcarchive/Products/Library/Frameworks/PromiseKit.framework" \
    -framework "archives/PromiseKit-iphonesimulator.xcarchive/Products/Library/Frameworks/PromiseKit.framework" \
    -framework "archives/PromiseKit-watchossimulator.xcarchive/Products/Library/Frameworks/PromiseKit.framework" \
    -framework "archives/PromiseKit-watchos.xcarchive/Products/Library/Frameworks/PromiseKit.framework" \
    -output "xcframeworks/PromiseKit.xcframework"
```


