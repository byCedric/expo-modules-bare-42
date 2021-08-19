# Notes

- `expo` has direct dependencies on unimodules, had to add a resolution
  - `@unimodules/core@~7.1.1`
  - `@unimodules/react-native-adapter@~6.3.4`
- `expo-modules-core@0.2.0` is added as nested dependency through `react-native-unimodules@0.14.6`, had to add a resolution
  - `react-native-unimodules`
  - `expo-constants`
  - `expo-file-system`
  - `expo-font`

# Issue

This doesnt work because it runs into an error in `expo-error-recovery`, related to `expo-modules-core`.

```json
"expo-modules-core": "0.3.0-alpha.0",
"expo-application": "file:../../../Projects/expo/expo/packages/expo-application",
"expo-constants": "file:../../../Projects/expo/expo/packages/expo-constants"
```

```zsh
> Task :expo-error-recovery:compileDebugKotlin FAILED
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryModule.kt: (6, 28): Unresolved reference: ExportedModule
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryModule.kt: (7, 28): Unresolved reference: Promise
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryModule.kt: (8, 39): Unresolved reference: ExpoMethod
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryModule.kt: (13, 52): Unresolved reference: ExportedModule
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryModule.kt: (16, 3): 'getName' overrides nothing
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryModule.kt: (18, 4): Unresolved reference: ExpoMethod
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryModule.kt: (19, 50): Unresolved reference: Promise
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryModule.kt: (26, 3): 'getConstants' overrides nothing
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryPackage.kt: (5, 28): Unresolved reference: BasePackage
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryPackage.kt: (6, 28): Unresolved reference: ExportedModule
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryPackage.kt: (8, 30): Unresolved reference: BasePackage
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryPackage.kt: (9, 3): 'createExportedModules' overrides nothing
e: /Users/cedric/Desktop/expo-unimodules-tests/bare-42/node_modules/expo-error-recovery/android/src/main/java/expo/modules/errorrecovery/ErrorRecoveryPackage.kt: (9, 62): Unresolved reference: ExportedModule
```

# Documentation issues

- `expo-modules-core` android gradle changes has a typo in the `@react-native-community/cli-platform-android` replacement
- Documentation doesn't say anything about replacements in `MainApplication.java`
  - remove all unimodules stuff from `MainApplication`
  - rename imported paths `org.unimodules.core` -> `expo.modules.core`

# Issue not updates dependencies

- `"expo-splash-screen": "~0.11.2",` does not have a newer version with renamed `org.unimodules.core` -> `expo.modules.core`
- `"expo-updates": "~0.8.1",` does not have a newer version with renamed `org.unimodules.core` -> `expo.modules.core`
