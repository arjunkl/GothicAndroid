# Rebuilding and relinking GothicAndroid 0.17

Download both the corresponding-source archive and the ARM64 relink-inputs archive
from the same release. Verify their SHA-256 values against SHA256SUMS.txt first.
The archives contain the detailed license inventory, source manifest, verification
record and a portable relink script. Preserve the third-party notices.

## Toolchain used

- Android NDK 27.2.12479018, ARM64, Android API 24 target
- Android SDK platform 35 and build-tools 35.0.0
- CMake 3.22.1, Ninja, JDK 17, Python 3
- Khronos glslangValidator 16.6.0
- Khronos Vulkan-Headers commit b26454f3ccd67e704117a39295fa13935fd3804c

Obtain tools from their official vendors or repositories. Set ANDROID_HOME,
JAVA_HOME and ANDROID_NDK_ROOT. Put glslangValidator and CMake on PATH. Set
VULKAN_SDK to the directory containing the pinned Vulkan headers.

From the extracted source directory:

```sh
INDEPENDENT_ICONS=1 PEWTER_ICONS=1 QA_APK=0 \
  VERSION_CODE=17 VERSION_NAME=0.17-preview \
  bash android/build-apk.sh
```

The script fetches the hash-pinned Java/native ZIP dependencies listed in
android/zip-dependencies.json. Use your own signing key via KEYSTORE; no original
release signing key is included or needed to modify and relink the software.

## Relinking

With the NDK installed and ANDROID_NDK_ROOT set, run the supplied relink/relink.py.
It combines the captured ARM64 application and library objects. Rebuild a modified
OpenAL archive or Bink source object from the corresponding source and replace the
relevant copied input before running the same relink recipe. The bundle documents
and verifies an example modified-Bink rebuild/relink.

To package a relinked engine, place it at BUILD_DIR/opengothic/libGothic2Notr.so and
run the APK script with PACKAGE_ONLY=1, the same icon/QA options, and your own key.
An APK signed with a different key cannot update the existing installation normally.
Export saves before any uninstall or app-data clearing.

## Verification scope

Captured-object relinking produced the exact engine bytes embedded in 0.17. A
modified Bink object was also compiled and successfully relinked. A sanitized
source tree completed a full native build; the final startup-log addition was
incrementally compiled separately. This is not a promise of a byte-identical full
APK build across different hosts, signing keys, tool versions or timestamps.
