# Installing Fabric

## Getting ready

If you're using v1.0, make sure to read the preparation info on [this page](../switching-mc-versions). Make sure to read the mods/shaders disclaimer as well.

## Installation (for v1.2 and below)

You'll need a few things:

* A working terminal or SSH client
* Filza File Manager
* The Fabric installer (.jar, not the .exe)

1. Download the Fabric installer from their website.
   - iOS 13 and later users: Open Files and locate the .jar, open the share sheet, and choose Open in Filza.
   
2. Take note of where Filza put the .jar. Chances are that it's in /var/mobile/Documents, but check just in case.

3. Open a terminal or SSH client and **make sure you don't `su` and become root with the next command!**

4. Due to a known issue with the Fabric installer, you'll need to be in the launcher's directory. Let's switch you to it with

```
cd /var/mobile/Documents/minecraft
```

5. Next, type this command to install Fabric (if you symlinked Java as explained on the installing page, you can just type `java`):

```
/usr/lib/jvm/java-16-openjdk/bin/java -jar /path/to/fabric-installer-XXX.jar client -dir . -mcversion version

# Change /path/to/ to where the jar actually is (i.e. /var/mobile/Documents),
# version to the version you want to install (i.e. 1.16.5),
# and XXX to the name of the Fabric installer (i.e. fabric-installer-0.7.4.jar)
```

**Tip:** If you don't want all of the output, add `> output.log` to the end of the command.

**Note:** As of the current release, you can only install and use 1.16.5.

6. Once complete, you can exit your terminal and open Filza again, this time moving to /var/mobile/Documents/minecraft and opening a preview of `launcher_profiles.json`

7. Copy the text that's in qoutes and to the right of `lastVersionId` and paste it into the version select screen.

## Installation (for v2.0)

We’re glad to announce that the mod installer is now available on PojavLauncher iOS! It’s GUI-based, so now you can install a wide range of mod loaders with just a few clicks from your screen!

![](https://camo.githubusercontent.com/1e5942f08a5ace38d85010dbb8181efd69ca149985da68d39f66d4785d42b09b/68747470733a2f2f63646e2e646973636f72646170702e636f6d2f6174746163686d656e74732f3833353830323833333837383132323537372f3930363230373639313231373731393239362f494d475f303237362e6a7067)

To install Fabric from the mod installer, you need to install openjdk-8-jre package from Doregon’s repo. After the installation, here’s what you need to do:

1. Download the Fabric installer from their [website](https://fabricmc.net/use/).

2. After downloading the file, save it to **Files app.** 

3. Open the launcher, go to Options -> Launcher preferences and switch the Java version to 8. (The Options button is (•••) on iOS 14 and up.)

4. Reopen the launcher, go to Options. Now select ‘Launch a mod installer’.

5. Now you will be prompted to select the installer. Just choose the Fabric installer you have downloaded.

6. Follow the instructions shown in the screen.

Now Fabric is installed on your device. Simply reopen the launcher, choose the version and tap Play.
