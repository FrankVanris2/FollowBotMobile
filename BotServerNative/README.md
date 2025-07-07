# Installation

This section will guide you through setting up your development environment and installing the necessary dependencies to run the mobile application.

## Configure Environment Variables

For React Native to build your application with native Android code, you need to set up specific environment variables.

1.  Open the **Windows Control Panel**.
2.  Search for 'edit environment variables' and click on **'Edit environment variables for your account'**.
3.  Under 'User Variables', click on **New...** and create the following variables:
      * **Variable name**: `ANDROID_HOME`
          * **Variable value**: `C:\Android\sdk`
      * **Variable name**: `ANDROID_SDK_ROOT`
          * **Variable value**: `C:\Android\sdk` (This often points to the same location as `ANDROID_HOME` for simpler setups).
4.  Select the **`Path`** variable and click on **Edit**. A new window will pop up.
5.  Add the following path: `%ANDROID_SDK_ROOT%\cmdline-tools\latest\bin`.
      * *Note: Using `%ANDROID_SDK_ROOT%` makes the path more robust if you ever change your SDK root.*
6.  Click **OK** on all open windows to save the changes.

## Install Android SDK Command-Line Tools

The Android SDK command-line tools are essential for managing your Android SDK packages.

1.  Go to the official Android developers page: [Command Line Tools Only](https://www.google.com/search?q=https://developer.android.com/tools/releases/platform-tools%23downloads) and download the **Windows version** under "SDK Command-line Tools".

2.  **Unzip** the downloaded file into `C:\Android\sdk`.

3.  Inside `C:\Android\sdk`, you should now have a `cmdline-tools` folder. Create a new directory named `latest` inside `cmdline-tools`.

4.  Move all the contents (subdirectories and files like `bin`, `lib`, etc.) from the *initial unzipped `cmdline-tools` folder* into the newly created `C:\Android\sdk\cmdline-tools\latest` directory.

      * *After this step, the path to `sdkmanager` should be `C:\Android\sdk\cmdline-tools\latest\bin\sdkmanager`.*

5.  Open a **new command prompt window** (ensure it's not PowerShell, as environment variables might not refresh immediately in existing sessions) and navigate to `C:\Android\sdk\cmdline-tools\latest\bin`.

6.  Run the following commands to install necessary Android SDK packages:

    ```cmd
    sdkmanager "platforms;android-33" "build-tools;33.0.0" "emulator" "platform-tools"
    ```

      * *Note: `android-33` is a common target SDK. You might need to adjust this based on your project's `targetSdkVersion` in `android/app/build.gradle`.*
      * `build-tools;33.0.0`: Specifies the build tools version.
      * `emulator`: Installs the Android emulator.
      * `platform-tools`: Installs adb and other essential tools.

7.  **Update all installed SDK packages**:

    ```cmd
    sdkmanager --update
    ```

## Build and Run the Android Version

Once your environment is set up, you can build and run the application.

1.  Navigate to your project's root directory (e.g., `BotServerNative` or `FollowBotNative`) in your terminal:

    ```bash
    cd YourProjectDirectory
    ```

2.  Install the project dependencies:

    ```bash
    npm install
    ```

3.  Connect your Android device to your computer via USB (ensure **USB Debugging** is enabled on your device). Alternatively, start an Android emulator.

4.  Build and run the application on your connected device/emulator:

    ```bash
    npx react-native run-android
    ```

      * This command will automatically start the Metro server if it's not already running.

-----

# Development Workflow

## Start the Metro Server (if needed)

The Metro server bundles your JavaScript code and serves it to your app. If `npx react-native run-android` doesn't start it automatically or you're running into issues, you can start it manually.

1.  In your project's root directory (`YourProjectDirectory`), run:

    ```bash
    npm start
    ```

2.  If Metro is running and the app isn't showing, you might need to press `a` in the Metro bundler's terminal window to run on Android, or `r` to reload the app on your device/emulator.

-----

# Debugging the Application

React Native provides built-in debugging tools.

  * On your physical device, **shake the device** to bring up the Developer Menu.
  * On an Android emulator, press `Ctrl+M` (Windows/Linux) or `Cmd+M` (macOS).

From the Developer Menu, you can select **'Open DevTools'** to launch a debugger window in your browser.

