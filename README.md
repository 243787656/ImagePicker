## ImagePicker
A simple library to pick images from the gallery and camera.

[![](https://jitpack.io/v/nguyenhoanglam/ImagePicker.svg)](https://www.jitpack.io/#nguyenhoanglam/ImagePicker)

## Screenshot
![device-2016-08-06-004242](https://cloud.githubusercontent.com/assets/4979755/17445822/b11d2288-5b70-11e6-914d-a15a4e956f4c.png)

## Download
Add it to your module's build.gradle with:
```java
allprojects {
    repositories {
        maven { url "https://jitpack.io" }
    }
}
```

and:
```java
dependencies {
    compile 'com.github.nguyenhoanglam:ImagePicker:1.0.0'
}
```

## How to use
### Start image picker activity
- Quick call
```java
ImagePicker.create(this)
            .single() // single mode
            .limit(10) // multi mode (default mode)
            .showCamera(true) // show camera or not (true by default)
            .origin(images) // original selected images, used in multi mode
            .start(REQUEST_CODE_PICKER); // start image picker activity with request code
```                
- Or use traditional Intent
```java
Intent intent = new Intent(this, ImagePickerActivity.class);

intent.putExtra(ImagePickerActivity.INTENT_EXTRA_MODE, ImagePickerActivity.MODE_MULTIPLE);
intent.putExtra(ImagePickerActivity.INTENT_EXTRA_LIMIT, 10);
intent.putExtra(ImagePickerActivity.INTENT_EXTRA_SHOW_CAMERA, true);
intent.putExtra(ImagePickerActivity.INTENT_EXTRA_SELECTED_IMAGES, images);

startActivityForResult(intent, REQUEST_CODE_PICKER);
```        
### Receive result

```java
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    if (requestCode == ImagePickerActivity.REQUEST_CODE_PICKER && resultCode == RESULT_OK && data != null) {
        ArrayList<Image> images = data.getParcelableArrayListExtra(ImagePickerActivity.INTENT_EXTRA_SELECTED_IMAGES);
        // do your logic ....
    }
}
```
#Thanks
- Darshan Dorai for [MultipleImageSelect](https://github.com/darsh2/MultipleImageSelect) 
- [Glide](https://github.com/bumptech/glide)
