# Setup

---

#### GitHub

1. Go to [GitHub](https://github.com/signup). Create an account using your personal email account. If you already have an account then just log into it.

2. Navigate to my [repository](https://github.com/MathPerson727/RobotProgrammingForDummies). You should be faced with this hotbar. Click the fork button.<img src="file:///C:/Users/dzhu3077/AppData/Roaming/marktext/images/2026-04-13-10-25-09-image.png" title="" alt="" data-align="center">

3. Once you get to the fork screen, keep all the default settings and create the fork. This will make your own version of the repository, so that you can make changes without messing with the original. Keep the tab of your forked repo open, we will use it in the next section.

#### Android Studio

1. Go to the [Android Studio](https://developer.android.com/studio) download page. Download the installer for Android Studio.

2. Open the installer, click through the installer using all default settings until it begins installing.

3. Once Android Studio finishes installing, open up the program. You should be looking at a window that looks like this:<img src="file:///C:/Users/dzhu3077/AppData/Roaming/marktext/images/2026-04-09-13-20-54-image.png" title="" alt="" data-align="center">

4. Hit the 'Clone Repository' button, which will open this window. <img src="file:///C:/Users/dzhu3077/AppData/Roaming/marktext/images/2026-04-09-13-19-51-image.png" title="" alt="" data-align="center">

5. In the URL bar, copy and paste your own forked GitHub repository. Press clone. This will create a local repository on your computer containing all of the information and history on your cloned repository.

**Your Android Studio project is now ready for you to work on.**

#### ADB WiFi

This is the Android Studio plugin that we will be using to remotely connect to the robot.

1. Open up your Android Studio project. Once you are there, click the 4-bars icon in the top left, and navigate File>Settings>Plugins.

2. Type ADB Wi-Fi in the plugin search bar, and install the plugin by Yury Polek.

#### Control Hub Setup

Your Control Hub is the device that will allow you to interface your code with your hardware. For now, we're just going to power it on and ensure that it's up to date.

1. Grab a battery from the battery case. If you have no clue where the batteries are at, then ask Barnes and pray that the batteries are charged.

2. Plug in the battery. The plug for the battery should be a distinct yellow socket that matches the battery's cable. When plugged in, the LED on the hub will flash blue, signifying the startup period. When it turns green, we know that it has fully initiated.

3. In order to connect it with our Android Studio, we need to manually wire into it for the first time, using a USB cable. This will define the control hub and make it recognizable for remote connection in the future. To ensure that this connection was actually made, unplug the control hub from your computer and click the Wi-Fi icon on the righthand side of the screen. A disconnected Control Hub should now show up in the tab.<img src="file:///C:/Users/dzhu3077/AppData/Roaming/marktext/images/2026-04-09-14-12-51-image.png" title="" alt="" data-align="center">

**In the future, when trying to connect remotely, you must connect to the control hub's Wi-Fi, which can be connected to the same way you'd connect to any other Wi-Fi. The default name will be something along the lines of 'FTC-####', and the default password is just 'password'.**


