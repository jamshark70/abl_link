# abl_link~

Ableton Link integration for Pd. Make sure to clone this repository recursively so you'll have all submodules.

## Desktop version

Users:

* Simply install `abl_link~` from deken and check out the help patch.

Developers:

* Build the external by saying `make` in the `external` directory and install it like any other external.
* Run the metronome patch in `abl_link/external` to check the timing of the external against the LinkHut sample app.

## Android version

Building and running the sample app is still a multi-step process. You need to be set up for native Android development and you'll need to modify some C++ code. If you'd like to add Link to your own app, check out the README in the `android` directory.

* Set up your build environment following these instructions: https://developer.android.com/studio/projects/add-native-code.html
* Clone Pd for Android and set it up to build from source (just adding a dependency via jcenter is not enough): https://github.com/libpd/pd-for-android#using-android-studio
* Clone this repository into the same parent directory as Pd for Android. (You can put it somewhere else, but then you'll have to adjust `android/CMakeLists.txt` accordingly.)
* Resolve build errors by adjusting the Link source code: Replace `std::llround` by `llround` in `link/include/ableton/link/Beats.hpp` and `link/include/ableton/link/Tempo.hpp` and delete the invocation of `to_string` in `include/ableton/discovery/Payload.hpp`.
* Now you should be able to build and run the sample app.

## iOS version

The iOS version is here: https://github.com/libpd/pd-for-ios