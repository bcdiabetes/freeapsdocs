## Summary

!!! info "Time Estimate"
    - 60-80 minutes for first time builders
    - 10-15 minutes for repeat builders

!!! abstract "Summary"
    You will:

    * Run the Build Select Script to download Loop code
    * Prepare to build the Loop app
    * Press the Xcode Build Button to build Loop
    * Watch in awe as you build your very own Loop app

!!! question "FAQs"
    * **Why does Xcode show a colorful spinning icon and not respond to me?** Unfortunately, sometimes Xcode gets confused and you need to force quit the application. See [Xcode Not Responding](../build/build_errors.md#xcode-not-responding) for instructions.
    * Many more FAQs for building Loop are in-line with the steps that trigger the questions.

## Build Video

The Loop and Learn team prepared this [YouTube video](https://youtu.be/gddhljzsNkM) showing how to build Loop 2.2.x including the steps required to update if you previously built. The steps are different now. The video may be worth watching, but once you've reviewed it, work through the new build process described on this page.

## GitHub Build Loop

If you previously used [GitHub Build](../gh-actions/gh-overview.md) to install Loop on this phone, you must make sure that automatically install is **disabled** in [TestFlight](../gh-actions/gh-deploy.md#install-testflight), or you will not be able to install on that phone with Xcode.

## Developer Mode

If you are running iOS 15 or watchOS 8 and earlier, you do not have developer mode and can skip ahead to [Download Loop](#download-loop).

New with iOS 16 and watchOS 9, you must enable Developer Mode to run or build Loop. (This is true for any app created by Xcode directly on your device.) If you want to know more, click on this [Apple Link about Developer Mode](https://developer.apple.com/documentation/xcode/enabling-developer-mode-on-a-device).

**Loop will not run until you enable Developer Mode for iOS 16.**

### Prepare your Phone and Watch

* If you are running Loop and update to iOS 16 and watchOS 9; Loop will no longer run until you enable Developer Mode and you will see a message similar to the next graphic

* If you are building to a new Apple Watch - you must first build the app with Xcode before the developer mode will be available.

    ![phone message if trying to run xcode app without developer mode enabled](img/phone-developer-mode-required.jpeg){width="300"}
    {align="center"}

* If your device uses iOS 16 (and watchOS 9); you must enable Developer Mode to build an app on that device using Xcode or it will show up as an "Unavailable Device" under Xcode

    ![xcode message for device without developer mode enabled](img/xcode-developer-mode-not-enabled.svg){width="450"}
    {align="center"}


#### Developer Mode on iOS 16 Device

To determine if Developer Mode is enabled, go into your phone settings, choose Privacy & Security, scroll to the bottom of the screen and tap on the Developer Mode row and examine the Developer Mode slider.

* If Developer Mode is enabled, the slider will be green and no further action is required
* If Developer Mode is not enabled, the slider will be blank
    * Move the slider so it is green
    * Reboot the device when asked
    * After the reboot, you will be asked if you want to turn on Developer mode
    * Tap on the `Turn On` option

#### Developer Mode on watchOS 9 Device

!!! warning "Build, Enable, Build"
    Reports from users indicate that when you are building to a new Apple Watch - you must first build the app with Xcode before the developer mode will be available. So plan to build with Watch paired, and then enable Developer Mode and build again.

This must be configured on the watch itself (not the watch app on the iPhone). To determine if Developer Mode is enabled, look at the watch face icons and find the Settings icon. Tap on it and scroll to and tap the Privacy & Security icon. Then scroll to the bottom and tap on Developer Mode.

* If Developer Mode is enabled, the slider will be green and no further action is required
* If Developer Mode is not enabled, the slider will be blank
    * Move the slider so it is green
    * Reboot the device when asked
    * After the reboot, if you are asked if you want to turn on Developer mode
    * Tap on the `Turn On` option

## Download Loop

This page has the detailed steps to run the Build Select Script to download the Loop code, prepare your computer and build Loop.

### Open Terminal

Go to the Finder app, click on Applications, then open the Utilities folder.  Locate the Terminal app and double-click Terminal to open a terminal window. The terminal window is very plain looking when you open it. That is normal.

#### Ensure a Year

!!! danger "Rebuild / Update on Same Computer?"
    If you used this same computer to build Loop previously and you did not delete provisioning profiles - you will not get a full year with this build.

    If you missed doing the [Updating: Delete Provisioning Profiles](updating.md#delete-provisioning-profiles), do that step now and return to this page.

    or more experienced folks may want to just paste this command into their terminal:

    ``` title="Copy and Paste to remove Provisioning Profiles"
    rm ~/Library/MobileDevice/Provisioning\ Profiles/*.mobileprovision
    ```

### Build Select Script

* With the release of Loop 3, the build process is different and simpler
    * Please read each step as if you are a new builder
    * Don't assume you know what you are doing
    * [FreeAPS](https://www.loopandlearn.org/freeapsdoc) is no longer supported by the Build Select Script
    * [Loop 3 with Patches](https://www.loopandlearn.org/github-lnl-patches) is provided instead

These instructions show each step needed to download Loop using the Build-Select script.

!!! note "Optional"
    The Build Select Script can also be used to build a companion app, called Loop Follow, and a fork of Loop, which has selected patches added. Follow these links to different websites for more information about those options.
    
    For those used to seeing FreeAPS here, it has been removed from the Build Select Script.
    
    Consider using Loop 3 as designed. If you need Libre or want the CustomTypeOne patches, those are provided in the Loop with Patches selection in the Build Select Script.
 
     * Information about [Loop Follow](https://github.com/jonfawcett/LoopFollow#readme)
     * Information about [Loop with Patches](https://www.loopandlearn.org/build-select/)
 
     You do not need to know about these options to build Loop.

Copy the line below that starts with `/bin/bash` by hovering the mouse near the bottom right side of the text and clicking the copy icon (should say Copy to Clipboard when you hover over it). When you click the icon, a message that says “Copied to Clipboard” will appear on your screen.

```title="Copy and Paste to start the BuildLoop.sh script"
/bin/bash -c "$(curl -fsSL \
  https://raw.githubusercontent.com/loopnlearn/LoopBuildScripts/main/BuildLoop.sh)"
```

Paste the line of text into Terminal. Be sure to click anywhere in the terminal before trying to paste. (Ways to paste: CMD-V; or CNTL-click and select from menu or Edit-Paste at top of Mac screen.)

Read the screen (shown below).  Type 1 and return if you understand the warning and agree.

* Please read what is on the screen as you progress.
* Adjust font size as directed if you have difficulty seeing the directions.

![paste the script line into terminal](img/bss-01-initial-message.svg){width="700"}
{align="center"}

Next you will see an introduction to the Build-Select script.  Please read this.  To build Loop, you will select the Build Loop option by typing 1 and return.

![choose to build Loop](img/bss-02-menu-message.svg){width="700"}
{align="center"}

Next you are asked which version of Loop you would like to build. Type 1 and return to build Loop (as shown in the graphic below) or 2 for the fork of Loop with added Libre CGM options and CustomTypeOne patches.

![choose which Loop to build](img/bss-03-choose-fork.svg){width="700"}
{align="center"}

### XCode Errors with Build-Select

!!! warning "WARNINGS"

    If you see errors like these . . .

    * `xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun`
    * `xcode-select: Failed to locate 'git', requesting installation of command line developer tools`
    * `xcode-select: error: tool 'xed' requires Xcode`

    You missed one of these steps:

    * [Install Xcode](step8.md)
    * [Xcode command line tools](step9.md#command-line-tools)

### Wait for Download to Complete

This download can take from 3 minutes to 30 minutes depending on your download speed.  You can leave the room and return later to check on progress. When you read the words in the terminal, as the script runs, you may see terminology you do not understand - don't worry - you do not need to understand enumeration or submodule or cloning.  You only need to review the display to look for any error messages. 

The next graphic shows terminal messages for the beginning of a successful download.

![the beginning of the clone for LoopWorkspace ](img/build-select-07.png){width="700"}
{align="center"}

When the download completes, the "Check for successful download" message is displayed as shown in the graphic below. You will need to scroll up in the terminal window to look through all the messages output to the terminal from the beginning of the download. (Your messages that start with "Submodule path" may differ.)

![download complete - search for errors message](img/bss-06-search-for-errors.svg){width="700"}
{align="center"}

If you do not find the word error in your terminal window, continue with [Download was Successful](#download-was-successful).

If you see the word "error" in your terminal window:

* Read the error message
* Try to figure out the problem
* If you need help, reach out to your favorite [Loop Social Media](../intro/loopdocs-how-to.md#how-to-find-help) site
* Tap any key other than 1, followed by return to cancel

### Download was Successful

If there are no errors, type 1 in the terminal window to continue. At this point you choose how to sign the targets, so first an explanation.

## Sign Targets

!!! question "What does Sign Targets Mean?"
    "Sign Targets" in Xcode identifies who built the app. You cannot deploy an app to a phone if you do not sign each target associated with that app.

!!! tip "Experienced Builders"
    This replaces several of the steps that used to be required to build Loop.

The first time you use the script, you will be asked how you want to sign the targets. If you have previously run the script and configured your computer to have a permanent file that contains your Apple Developer ID, this question will not be shown. Skip ahead to [Review LoopConfigOverride.xcconfig](#review-loopconfigoverridexcconfig).

The next question, as shown in graphic below, is whether you will (1) Sign Automatically or (2) Sign Manually.

* If you are building with a paid developers account, choose option 1, and continue on this page
* If you are building with a Free option or plan to build to a simulator on your computer, choose option 2 and click on [Build Free Loop](build-free-loop.md) to move to the page with those instructions

![messages for choosing Sign Automatically or Sign Manually](img/build-dev-b-01-choose.svg){width="700"}
{align="center"}

