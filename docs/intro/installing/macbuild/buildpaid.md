{%
   include-markdown "buildstub.md"
%}

### Paid Developer Account

Continue with this page only if you have a paid developer account.

* You need to switch to the [Loop Free Build](build-free-loop.md) page for a free account.

### Create Permanent LoopConfigOverride.xcconfig

The following graphics show the terminal display after selecting option 1 to use Apple Developer ID.

* Graphic below:
    - User is presented with instructions for getting Team ID from the Membership page
        - After review, the user hits return

![instructions for obtaining developer id](img/build-dev-b-01-a.svg){width="700"}
{align="center"}

* Graphic below:
    - The instructions remain on the screen for reference
    - The developer.apple.com web page (not shown) opened automatically in the browser after user hit return
        - User obtains ID
    - User enters ID in terminal and then hits return

![entry of developer id](img/build-dev-b-01-b.svg){width="700"}
{align="center"}

After hitting return, the user can verify the entry.

### Review LoopConfigOverride.xcconfig

!!! note "Use Your Team ID"
    The ID, 0123456789, shown in the graphic below is for illustration purposes only. Your terminal display shows your Apple Developer ID (the Team ID on the Membership page).

If you previously built with this computer using the script, you already have the file configured. The review step is the same each time.

* Graphic below:
    - The developer ID stored in the permanent file is displayed for review
    - After review, hit return to continue and [Plug in Your Phone](#plug-in-your-phone)
    - OR - to modify the ID in the file, see [Problem with the ID?](#problem-with-the-id)

![review of override file before use](img/build-dev-b-03.svg){width="700"}
{align="center"}

#### Problem with the ID?

If there is a problem with the ID that is stored on your computer, you can modify it before continuing.  The instructions, shown in the terminal message, are repeated here:

To edit the LoopConfigOverride.xcconfig file with a different developer ID:

1. Open finder, navigate to Downloads/BuildLoop
1. Locate and double click on LoopConfigOverride.xcconfig
    * This will open that file in Xcode
1. Edit in Xcode and save file

You can now return to the terminal and hit return for the next step.

## Build Loop

### Plug in Your Phone

Refer to the graphic below. The messages in the terminal instruct you to:

* Unlock your phone
* Plug Phone into the computer
    * (Optional) If you have an Apple Watch that has never had Loop on it
        * Make sure watch is paired, unlocked and on your wrist
    * If you have never "Trusted" this computer with these device(s), do so now
        * A screen will pop up on your phone (and watch) asking if you trust the computer
        * Select "Trust"
        * After trusting phone and watch, phone should remain plugged in, but watch does not need to stay in proximity of the phone
* Now you are ready to hit return in the terminal window

![script instructions for plugging in phone and trusting computer on phone and watch](img/build-dev-b-04.svg){width="700"}
{align="center"}

The next action of the script is to 

* Open a browser window displaying this section of LoopDocs
* Open Xcode

The final script message informs you that you can close the terminal window.

* Wait until you've successfully built the app before closing the terminal


### Initial Xcode Screens

!!! warning "watchOS Simulators"
    Yes, watchOS simulators are required to build Loop. If Xcode asks if you want to download them - say yes. It's slow but you cannot build Loop without the simulator.

    *   Tap on [New with Xcode 14](../build/build_errors.md#new-with-xcode-14) for more information

First select Loop (Workspace) and confirm your phone is selected. Refer to the GIF below and follow the directions:

* Frame 1:  Xcode screen opened by the script after a fresh download
    * **Fresh Download? Wait for indexing to begin**
        * If you see messages about fetching symbols or resolving packages, please wait until you see the Indexing message as shown in the GIF below just to the left of the dashed-blue rectangle
    * The red rectangle indicates where you will change Loop to Loop (Workspace)
    * The red x in the dashed-blue rectangle region indicates you need to fix a problem before building
* Frame 2: Inset shows the action needed to select Loop (Workspace)
* Frame 3: Loop (Workspace) selected but there's a red x in the dashed-blue rectangle region

![gif showing the initial xcode screens following fresh download](img/xcode-build-loop3-a.gif){width="750"}
{align="center"}

!!! warning "Most Common Mistake"

    - The most common mistake in this step is:
        - not selecting Loop (Workspace)
        - not selecting your actual phone

### Package Dependency Error

If there is no red x in the dashed-blue rectange region on your Xcode screen, skip ahead to [Start Build](#start-build) on this page.

Otherwise, tap on the red x in the dashed-blue rectange region:

* If your screen is similar to the figure below, perform the [Fix for Package Dependency](#fix-for-package-dependency) (instructions are repeated on this page for convenience; duplicated on Build Errors page)
* If you have a different error, search the [Build Error](build_errors.md) page

![gif showing the xcode screens with dependency error](img/xcode-build-loop3-b.svg){width="750"}
{align="center"}

### Fix for Package Dependency

1. Click on the folder icon (indicated by red square)
1. Hold down the Control-Key and click the `Package Dependency` row to display the dropdown menu (shown in the inset)
1. Select Resolve Package Versions from the dropdown menu
1. Once that completes, the red x should resolve and you can build as soon as the Indexing message appears

![package dependency solution](img/xcode-package-dependency-solution.svg){width="600"}

### Start Build

The first time you build, there will be steps that will not be required for subsequent builds. These are clearly marked in the intructions with the word **First-Time**.

Refer to the GIF below:

* Frame 1: Package Dependency resolved (no red x)
    * Xcode is Indexing as seen in dashed-green rectangle region
        * Indexing makes searching faster; it does not need to complete before building
    * Click the "Play" button highlighted by red rectangle to start the build
    * **First-Time for this Phone:** A Device isn't registered screen appears, as shown in the graphic below the GIF
        * This happens for any phone not registered to the selected Developer ID
        * You must be connected to the internet so the device can be registered
        * Click register and then the build will continue (as shown in the GIF)
* Frame 2: Build has started
    * Xcode is Building as seen in dashed-green rectangle region
    * **First-Time on This Computer:** 
        * Follow the [Always Allow Instructions](#codesign-keychain-access) the first time this Developer ID is used on this computer
        * Never hit Deny
* Frame 3: Build succeeded
    * App is running as seen in dashed-green rectangle region
    * If your phone locked during the build process, you will see a message to unlock your phone, as shown in the graphic below the GIF
        * Simply unlock your phone and Xcode does the rest
        * If you tapped on `Cancel Running`, just hit the build button again
    * **First-Time for this Phone:** You may also see a "Could Not Launch Loop" message
        * Follow the [Update Settings for Developer](#update-settings-for-developer)

![gif showing the xcode screens when building](img/xcode-build-loop3-c.gif){width="750"}
{align="center"}

![xcode display if phone is not yet registered to developer account](img/xcode-build-loop3-c-01a.svg){width="200"}
![xcode display if phone is locked](img/xcode-build-loop3-c-03a.svg){width="300"}

If the app opened on your phone, the next two sections for first-time builders are not needed.  Skip ahead to [Successful Build](#successful-build).

If you got red error messages, skip ahead to [Build Failed?](#build-failed)

#### Codesign / Keychain Access

!!! abstract "First Time Using Developer ID on Computer"

    During your first build with a given Developer ID on your computer, you will see a codesign/keychain access prompt, as shown in the graphic below. Enter the same password you use to log in to the mac, select "Always Allow" and then do it again each time you are asked.

    ![img/keychain-prompt.png](img/keychain-prompt.png){width="350"}
    {align="center"}

    It is normal for this prompt to come up repeatedly even after you enter the correct password (once for each target Loop needs to sign).

    In frustration, people think the prompt must be broken because it keeps reappearing and press deny or cancel. **Don't press deny.** Keep entering your computer password and pressing the "Always Allow" button as many times as it takes. The build will then continue.

    **FYI:** _codesign is for code sign - nothing to do with design._

#### Update Settings for Developer

!!! abstract "First Time Building on a New Device?"

    If this is the first time you have installed an app on your iPhone using a free account, you will see warnings in both Xcode and on your phone after a successful build and install on your phone.

    Don't worry, dismiss the messages and do this extra step on the phone. These instructions are valid for iOS 15:

    * Open Phone Settings
    * Select General
    * Select VPN & Device Management
    * Under the Developer App section, tap on icon
    * Tap on Trust
    * You should now be able to open the app

    ![messages shown in Xcode and on the phone for untrusted developer](img/trust_device.svg){width="400"}

    ![untrusted developer on phone](img/trust_device_2.svg){width="200"}

### Build Failed?

No red error messages? Skip ahead to [Successful Build](#successful-build).

!!! bug "Red Errors"
    If you get a message that your build failed and see **RED ERROR** messages:

    * Go to the [Build Errors](build_errors.md) page to find the steps to fix your build error
    * (Optional) Follow the [Clear the Error Message](#clear-the-error-message) process
    * Return to [Start Build](#start-build) to try again

!!! question "FAQ: But what about those yellow or purple warnings that remain in Xcode? Should I worry about them?"

    If you see yellow or purple warnings after your build is done...those are not an issue. Don't try to resolve them or fret about them. They mean nothing to the successful use of your Loop app.

    ![img/yellow-warnings.png](img/yellow-warnings.png){width="600"}
    {align="center"}


#### Clear the Error Message

Once you've resolved a build error and start the build process again, Xcode will continue to show a red indicator on the top line from the previous failure.  If you don't like seeing that, clean the build folder to clear the error.  Otherwise, as long as the steps of the build are showing across the top line, Xcode is still working on the build.  When the build succeeds, the red circle will disappear.

!!! abstract "Clean Build Folder"

    * In Xcode menu, select Product, then Clean Build Folder
    * Wait for cleaning to complete: you'll see a "Clean Finished" message

### Successful Build

After you see the Loop app open on your phone, you can unplug your phone and acknowledge the Xcode message: `Lost connection to the debugger on . . .`.  The square icon next to the play button goes away as soon as you unplug your phone from Xcode.

The Loop app on your phone closes (but does not quit) when you unplug the phone. Open the Loop app on your phone just to be sure.

!!! success "Congratulations!"
    
    ![alt](https://media.giphy.com/media/l0MYt5jPR6QX5pnqM/giphy.gif)


If you plan to build again on a backup phone, or want to try a customization, easiest for you to leave Xcode open. Otherwise, you can quit out of Xcode now.

## Protect that App

!!! danger "Protect Against Deletion"
    Prevent your Loop app from being deleted accidentally.

    If you, or a child, deletes the app from the home screen, it is gone - you have to rebuild and reenter all settings and start a new pod or add back in your Medtronic pump.

    The steps vary depending on iOS. With iOS 15 and 16, it is under Screen Time, Content & Privacy Restrictions, iTunes & App Store Purchases, Deleting Apps. Choose Don't Allow. If those steps don't help, do an internet search like this, where you use your current phone iOS version number:

    * "turn off app deletion iOS ##"
    * "iOS ## prevent app deletion"

    Follow the instructions to prevent deletion of what is now a critical medical app.

## IMPORTANT SAFETY REMINDER

* **STAY IN OPEN LOOP UNTIL YOU UNDERSTAND THE SYSTEM**
* Do NOT skip the Set Up and Operate material; at least skim it.
* Keep reviewing LoopDocs - some material will be more impactful once you have the app in your hands.
* Ask [questions](../intro/loopdocs-how-to.md#how-to-find-help) if you are confused.
* Learn to use the [LoopDocs search feature](../intro/loopdocs-how-to.md#website-search)

### New to Loop 3

If this is your first build with Loop 3, head to the Set Up tab starting here: [Loop 3 Overview](../loop-3/loop-3-overview.md).

!!! tip "Pro Tip: Read Along in LoopDocs as you Onboard"
    One of the goals for Loop 3 is to make the app robust even if you don't read the documentation, but a lot of questions may be resolved if you read along in LoopDocs as you onboard.

    All those mentors who answer questions are volunteers.

Even if you don't read all the pages under the Set Up tab now, these links are important.

* New Looper: [Onboarding](../loop-3/onboarding.md)
* Building Loop 3 over Loop 2.2.x or FreeAPS: [Experienced Looper Onboarding](../loop-3/onboarding.md#experienced-loopers)

!!! info "Add a Calendar Reminder"

    - It is good practice to add a reminder to your calendar when the app will expire
    - Be sure to add an alert to that reminder so you have enough time to do all the [Loop Updating](updating.md) steps to build the app again before it expires
    - Even better, practice building every 3 to 6 months so you don't forget and keep that expiration date far in the future

## Optional Steps

### Code Customizations

**New Loop users**: Customizations are not a required part of any Loop build. As you gain experience using your Loop app, you may want to customize some of the features. First time builders are encouraged to build with the standard, default code. You can always update your Loop app to add customizations at a later time, using the same download. Subsequent build time is much faster than the initial build for a given download.

!!! tip "Pro Tip"
    With a fresh download of code, it's always best to build without customization to ensure the build works without errors.

To add custom configurations to your Loop or Loop Apple Watch apps, follow the step-by-step instructions on the [Code Customizations](code_customization.md) page and then build the app again.


### Apple Watch

**Existing Apple Watch users**: Please update your watchOS prior to building the Loop app.  The current version of Loop requires watchOS 4.1 or newer.

**New Apple Watch users**: If you have an Apple watch and want to use it with Loop, first pair the watch with the iPhone before continuing to the next steps.  If you get a new watch after building the Loop app, you'll need to redo your Loop build.


### Build Again with this Download

Follow the [Find My Downloaded Loop Code](code_customization.md#find-my-downloaded-loop-code) instructions if you later wish to build with this same dowload. Plug in an unlocked phone and start at the [Start Build](#start-build) section of this page. You may need to select the phone you just plugged in. Everything else should be ready for you the start the build process.

!!! warning "Don't use a really old download"
    Do not use a really old download.

    Check the date of your download against the latest [Current Release](..//version/releases.md#current-release) date and decide whether to get a fresh download instead.

