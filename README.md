Android FingerprintCompat Library
========
A wrapper library to simplify fingerprint authentication on Android with a backward compatibility prior to Android M.

Download
--------
Grab it via Gradle:

**Step 1:** Add the JitPack repository to your build file
```groovy
repositories {
    maven { url 'https://jitpack.io' }
}
```
**Step 2:** Add the dependency
```groovy
compile 'com.github.sTatiyanupanwong:android-compats-fingerprint:1.0.0'
```

Usage
--------
1. Add android.permission.USE_FINGERPRINT in AndroidManifest
```xml
<uses-permission android:name="android.permission.USE_FINGERPRINT"/>
```

2. Call FingerprintCompat APIs

The following are FingerprintCompat APIs to interact with fingerprint service
```java
FingerprintCompat.of((Context) this).authenticate((AuthenticationCallback) this);
FingerprintCompat.of((Context) this).encrypt((EncryptionCallback) this);
FingerprintCompat.of((Context) this).decrypt((DecryptionCallback) this);
```

To check availability of fingerprint service, safe guard by

```java
if (FingerprintCompat.isAvailable(this)) {
    // Call API here...
}
```

or explicitly handle from callback, for instance,

```java
@Override
public void onAuthenticationFailed(Throwable throwable) {
    if (throwable instanceof FingerprintUnavailableException) {
        // Fingerprint unavailable...
    }
}
```

License
=======

```
Copyright (C) 2017 Supasin Tatiyanupanwong

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
