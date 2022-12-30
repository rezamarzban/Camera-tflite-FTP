# TensorFlow Lite Object Detection FTP

### Overview

This is a camera app that continuously detects the objects (bounding boxes and
classes) in the frames seen by your device's back camera and send object image to FTP server, with the option to use
a quantized
[MobileNet SSD](https://tfhub.dev/tensorflow/lite-model/ssd_mobilenet_v1/1/metadata/2),
[EfficientDet Lite 0](https://tfhub.dev/tensorflow/lite-model/efficientdet/lite0/detection/metadata/1),
[EfficientDet Lite1](https://tfhub.dev/tensorflow/lite-model/efficientdet/lite1/detection/metadata/1),
or
[EfficientDet Lite2](https://tfhub.dev/tensorflow/lite-model/efficientdet/lite2/detection/metadata/1)
model trained on the [COCO dataset](http://cocodataset.org/). These instructions
walk you through building and running the demo on an Android device.

The model files are downloaded via Gradle scripts when you build and run the
app. You don't need to do any steps to download TFLite models into the project
explicitly.

This application should be run on a physical Android device.

![App example showing UI controls. Highlights a cat](https://storage.googleapis.com/download.tensorflow.org/tflite/examples/obj_detection_cat.gif)

## Releases

Ver 2.0.0 changes:

Added FTP action on object detection

Changed default values and selections in option to best

Downloaded tflite models to assets folder

Ver 1.0.0 changes:

Created repository

## Build

### Prerequisites

*   This sample has been tested on Android IDE and Colab.

*   A physical Android device with a minimum OS version of SDK 24 (Android 7.0 -
    Nougat) with developer mode enabled. The process of enabling developer mode
    may vary by device.

### Building

Run below commands in Colab:
```
!wget https://dl.google.com/android/repository/commandlinetools-linux-9123335_latest.zip
!mkdir -p sdk
!unzip commandlinetools-linux-9123335_latest.zip -d sdk
!yes | ./sdk/cmdline-tools/bin/sdkmanager --sdk_root=/content/sdk "tools"
!git clone https://github.com/marzban2030/Camera-tflite-FTP
!chmod -c 755 /content/Camera-tflite-FTP/gradlew
!export ANDROID_HOME=/content/sdk && cd /content/Camera-tflite-FTP && ./gradlew assembleDebug
```

Then run:
```
from google.colab import files
files.download('Camera-tflite-FTP/app/build/outputs/apk/debug/app-debug.apk')
```

### Models used

Downloading, extraction, and placing the models into the assets folder is
managed automatically by the download.gradle file.
