# QuickSwitch - Quickstep enabler for any supported launcher

QuickSwitch is a Magisk module which systemlessly enables Pie recents (Quickstep) in any supported launcher

![GitHub All Releases](https://img.shields.io/github/downloads/skittles9823/quickswitch/total?label=Downloads%20on%20GitHub)

## Changelog:

### v3.2.1
- support Magisk 24's update.json format

<details><summary>Older changes</summary>

### v3.2.0
- fix OOS for real

### v3.1.9.1
- move overlay to /vendor on OOS12+ (bruh moment)

### v3.1.8
- mark launcher as compatible if version name is same as system
- fix OnePlus display issues

### v3.1.7.1

- make sure module is enabled if the script is called
- show android version code (11) instead of android sdk (30) for incompatible launchers in the QuickSwitch app
- fix module on OOS 11 (Thanks to Mark455)

### v3.1.7

- save logs from the launcher patching process
- fix module on Android 11 - no longer needs manual fixing

### v3.1.6-4

- update QuickSwitch app to fix OOS issue where patching OnePlus Launcher duplicated the launcher after an app update

### v3.1.6-3

- change package/directory names of the overlay
- add flags to the overlays manifest that should have been there for a while
- hopefully these changes help with the magisk hide lag
- on uninstall, also reset the provider
- support patching OP Launcher 4.5.4 for swipe down shelf

### v3.1.6-2

- fix crash while grabbing logs from the app
- add patch version to the patched apk and prompt the user when the launcher needs to be patched again
- fix some typos and move some functions around in the script

### v3.1.6 - hotfix

- fix uninstalling the module through magisk manager causing /sdcard to fail to mount on next boot
- revert the commit which was supposed to uninstall the app when uninstalling the module as it did not work

### v3.1.6

- fix severe issue which causes /data/app/ to be deleted
- the app now has a button to share an archive of the log files for debugging
- fix dark mode in OnePlus launcher
- fix the overlay not getting compiled in some situations
- the app now sends the script variables in a better way to make the code much cleaner and easier to manage
- completely fix the drawer text colour, corner radious, and recents long press buttons in oneplus launcher

### v3.1.5 - Deleted

- more OnePlus launcher patching fixes
- add support for some custom roms to have dt2s and notification support in the patched OnePlus launcher
- clean up old unused code

### v3.1.4 - Deleted

- add a launcher patcher to the app with support for the OnePlus launcher. Now you can grab the latest stock apk from apkmirror and use the patcher to port it on device. (This can take several minutes to complete)
- add a dark mode toggle to the script (not implemented in the app yet)

### v3.1.3

- update QuickSwitch apk because i'm dumb and didn't update it to the latest version last time
- small update and optimisations to the logging scripts

### v3.1.2

- twrp doesn't like \n so lets make the abort error display correctly
- verify aapt successfully created the overlay, and abort otherwise
- fix for Q custom roms on Samsung devices

### v3.1.1

- abort installation when installed through recovery (the app won't get installed in that case anyway so lets just avoid complaints)
- update the app and backend script to show the user simple, but more accurate errors
- slightly clean up the install script

### v3.1.0

- fix switching providers on Samsung OneUI 2.0
- add sepolicy.rule so the logging can actually show if the overlay is active

### v3.0.9

- force the overlay to /product/overlay on Android Q and above
- preemptively check for Q or higher to support R when magisk adds support
- make the uninstall code wayyyyy simpler
- other various changes

### v3 0.8

- prepare to fix issues with Omni/PE and other roms using prebuilt vendor on OnePlus devices
- optimisations to the logging functionality

### v3.0.7

- fix not being able to switch providers after initial flash of the module

### v3.0.6

- install the QuickSwitch app as a user app - should fix issues with users not finding the app after install
- because of this, you can now flash the module and immediatly change providers with only having to reboot once

### v3.0.5

- fix for the launcher not getting copied over and aborting recents provider change
- fix dalvikvm invokation for Android 10 (-Xnodex2oat is removed upstream)

### v3.0.4

- remove selinux dependant commands in favour of grepping packages.xml and listing the contents of /data/app to find launcher dirs
- sign the overlay again
- I'd like to thank osm0sis@XDA for helping with this update

### v3.0.3

- fix provider resetting when updating the module

### v3.0.2

- attempt to fix bootloops on OnePlus devices

### v3.0.1

- fix small bug

### v3.0.0

- completely rewrite the app and the module backend. Now the app uses a shell binary as the backend to
  remove the need for bootscripts
- re-add the $MODDIR/product/overlay install path as the Magisk issue has been fixed
- added a check for MIUI which will abort the installation of the module

### v2.0.9

- add support for /oem/OP/OPEN_US/overlay/framework as the overlay dir
- temporarily reverted the /product change so Magisk canary users have a somewhat working QuickSwitch
- fix up inconsistent shell, it's all uniform now
- rewrite uninstall.sh so it works now (oversight on my part from before)
- actually make the module abort when it's flashed on an unsupported android version
- more miscellaneous fixes and optimisations

### v2.0.8

- quick hotfix for the while loop

### v2.0.7

- added check to prevent using Pie launchers on Q and vice-versa
- add while loop to hopefully make sure the overlay dir is created

### v2.0.6

- update is_mounted(\_rw) functions to match Magisks
- update apk and switch to a new reboot method
- updated /product logic for Magisk 19305+
- moved all bootscripts to /data/adb/service.d and /data/adb/post-fs-data.d so they will always get executed first
- more attempts at trying to fix magisk not successfully copying the overlay
- oopsie, forgot to add an API check again after switching templates

### v2.0.5

- fix grid recents

### v2.0.4

- fix rom info logging formatting
- check for /product being a symlink and copy the overlay systemlessly if it is
- add more checks in the late-start script so it isn't needlessly run every boot for devices with /product/overlay
- various improvements
- add grid recents toggle
- remove hyperion blacklist app side (will now show hyperion for everyone)

### v2.0.3

- fix major derp

### v2 0.2

- slight template update
- small change to make updating from 2.0.0+ not reset the recents provider
- back on the magisk repo

### v2.0.1

- hyperion is now public for all!

### v2.0.0

- switch to the new Magisk template. RIP rootless users
- overhauled basically everything
- remove device check and replace with a warning that RIL issues are rom side
- fix the creation of quickstepswitcher-old.log and clean up quickstepswitcher.log
- logs are now slightly more descriptive for me.
- more attempts to fix /product/overlay installs
- fix QuickSwitch creating multiple launcher dirs when ever the launcher gets an update
- add capability to set default home app

### v1.1.2

- move app back to /system/app as it was broken for some people in priv-app
- remove quickswitches privapp-permissions.xml file (toggling swipe up gestures in the app is likely broken now)

### v.1.1.1

- update to Unity 3.1
- update QuickSwitch APK, now can enable/disable navigation bar gestures
- copy logs to /sdcard/Documents/quickstepswitcher as well
- various fixes for resetting to the default provider
- temporarily disable installs on OnePlus3(T) devices as it causes RIL to die for unknown reasons

### v1.1.0

- fix recents provider not persisting after updating the module
- remove old apk

### v1.0.9-hotfix

- fix bootloop when resetting to default provider

### v1.0.9

- more /product/overlay fix attempts
- fix the bootscript error appearing even though the bootscript successfully ran
- add a warning when setting a systemized launcher as the recents provider
- add a way to reset the recents provider back to stock

### v1.0.8

- add debugging to the QuickSwitch app so its more user-friendly
- recents provider will persist on updates from now on
- another possible fix for devices with /product/overlay

### v1.0.7

- fix uninstallation of Lawnstep

### v1.0.6

- Unity 2.3 update
- bring back rootless installs
- remove lawnstep if detected in magisk

### v1.0.5

- rename to QuickSwitch
- begin troubleshooting /product/overlay installs

### v1.0.4

- fix app having issues acquiring root

### v1.0.3

- fix late-start script (uninstalling anyway the user wants actually works now)
- fix derp in config.sh

### v1.0.2

- updated QuickstepSwitcher app (improved info and fixed theme bugs)
- fixed switching providers not working (Android dir handling is dumb af)

### v1.0.1

- hotfix for uninstalls

### v1.0.0

- initial release

</details>
