# Student project for text recognition in poster images using Tesseract OCR in an Android App
Hochschule für Technik und Wirtschaft Berlin

# Authors
- Kevin Kretzschmar
- Lucas Pohling

# References
- [Android Studio][android-studio]
- [Tesseract][tesseract-ocr]
- [Tesseract documentation][Tessdoc]

# Requirements
- Installation of Android Studio (for Windows)
- Installation of Tesseract (for Windows)

# Files and purpose
## activity_main.xml
App layout, buttons, textview, etc. can be found here.

## MainActivity.java
Main code: app libraries and functions as well as tesseract integration can be found here.

## Tesseract4Android/tesseract4android/src/main/assets/eng.traineddata
## Tesseract4Android/tesseract4android/src/main/assets/deu.traineddata
Put the language traineddata file to be used by tesseract into this folder. Multiple files can be used, these have to be added in Main.Activity.java under
"tessBaseAPI.init(dataPath, "deu+eng");" Many different versions are e.g. available here: [traineddata1], [traineddata2]. Make sure you use this folder. 

## gradient_background.xml
App background layout gradient. Change startColor and endColor for different designs.

## AndroidManifest.xml
Change app name here.

## app/src/main/mipmap
Change app icon here in ic_launcher folders.

## Trouble Shooting
If "Run 'app'" does not work, check tesseract, android and traineddata versions and 'gradle build' and 'assemble' to make sure dependecies are correct. Emulator problems can usually be solved by trying out a different smartphone version and using 'cold boot now' in the AVD manager options.


[android-studio]: https://developer.android.com/studio
[tesseract-ocr]: https://github.com/tesseract-ocr/tesseract
[Tessdoc]: https://tesseract-ocr.github.io/
[traineddata1]: https://github.com/tesseract-ocr/tessdata
[traineddata2]: https://tesseract-ocr.github.io/tessdoc/Data-Files.html


FROM HERE ONWARDS FIND THE ORIGINAL FORKED READ.ME


# Tesseract4Android

Fork of tess-two rewritten from scratch to build with CMake and support latest Android Studio and Tesseract 4.

The Java/JNI wrapper files and tests for Leptonica / Tesseract are based on the [tess-two project][tess-two], which is based on [Tesseract Tools for Android][tesseract-android-tools].

## Dependencies

This project uses additional libraries (with their own specific licenses):

 - [Tesseract][tesseract-ocr] 4.1.1
 - [Leptonica][leptonica] 1.78.0
 - [libjpeg][jpeg] v9c
 - [libpng][png] 1.6.37

## Prerequisites

 - Android 4.1 (API 16) or higher
 - A v4.0.0 [trained data file(s)][tessdata] for language(s) you want to use. Data files must be
copied to the Android device to a directory named `tessdata`.
 - If you want to use PdfRenderer, copy also [pdf.ttf][pdffile] file to the `tessdata` directory.
 - Application must hold permission `READ_EXTERNAL_STORAGE` to access `tessdata` directory.

## Usage

To use Tesseract4Android in your project add dependency to your `build.gradle` file:

    dependencies {
        implementation 'cz.adaptech.android:tesseract4android:2.1.0'
    }

## Building

You can use Android Studio (tested on version 3.5.3) to open the project and build the AAR. Or you can use `gradlew` from command line.

To build the release version of the library, use task `tesseract4android:assembleRelease`. After successful build, you will have resulting `AAR` file in the `<project dir>/tesseract4Android/build/outputs/aar/` directory.

### Android Studio
 
 - Open this project in Android Studio.
 - Open Gradle panel, expand `Tesseract4Android / :tesseract4Android / Tasks / other` and run `assembleRelease`.

### GradleW

 - In project directory create `local.properties` file containing:
 
       sdk.dir=c\:\\your\\path\\to\\android\\sdk
       ndk.dir=c\:\\your\\path\\to\\android\\ndk
   
   Note for paths on Windows you must use `\` to escape some special characters, as in example above.
     
 - Call `gradlew tesseract4android:assembleRelease` from command line.

## License

    Copyright 2019 Adaptech s.r.o., Robert Pösel

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


[tess-two]: https://github.com/rmtheis/tess-two
[tesseract-android-tools]: https://github.com/alanv/tesseract-android-tools
[tesseract-ocr]: https://github.com/tesseract-ocr/tesseract
[leptonica]: https://github.com/DanBloomberg/leptonica
[jpeg]: http://libjpeg.sourceforge.net/
[png]: http://www.libpng.org/pub/png/libpng.html
[tessdata]: https://github.com/tesseract-ocr/tessdata/tree/4.0.0
[pdffile]: https://github.com/tesseract-ocr/tesseract/blob/master/tessdata/pdf.ttf
