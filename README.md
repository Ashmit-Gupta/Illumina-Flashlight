# Illumina Flashlight

**A simple and reliable Android flashlight app that utilizes your device's camera flash to illuminate your surroundings.**

- **Intuitive Toggle**: Effortlessly switch between flashlight on and off states.
- **Permission Management**:The Dexter library ensures smooth handling of camera access requests.
- **User-friendly Interface**: Clear visual feedback keeps you informed about the flashlight's status.

## Screenshots





## Permissions

This app requires the following permission:

- **Camera**: Grants access to the device's camera flash for illumination purposes.

## Using Dexter for Runtime Permission Handling

This app utilizes the [Dexter library](https://github.com/Karumi/Dexter) to simplify the process of requesting CAMERA permission at runtime. Here's a brief overview:

### Dependency inclusion

Add the Dexter library to your `build.gradle` file:
```gradle
dependencies {
    implementation 'com.karumi:dexter:6.2.3' // Replace with the latest version
}
```

### Requesting permissions

Dexter provides a concise API for requesting permissions. In this app, we utilize Dexter to request the CAMERA permission:
```java
Dexter.withContext(this)
	.withPermissions(
		Manifest.permission.CAMERA,
		Manifest.permission.READ_CONTACTS,
		Manifest.permission.RECORD_AUDIO
	).withListener(new MultiplePermissionsListener() {
	    @Override public void onPermissionsChecked(MultiplePermissionsReport report) {/* ... */}
	    @Override public void onPermissionRationaleShouldBeShown(List<PermissionRequest> permissions, PermissionToken token) {/* ... */}
	}).check();
```


## Handling Permission Results

The `MultiplePermissionsListener` interface provides methods for handling the results of the permission request. In our case, we check if the permission is granted and proceed with initializing the flashlight if so. Additionally, we display a toast message if the permission is denied.

## Benefits of Using Dexter

Using Dexter for runtime permission handling offers several advantages:

- Simplified permission request code compared to the traditional approach.
- Efficient handling of multiple permission requests.
- Options for handling permission rationales.
- Built-in error handling capabilities.
