# Basic troubleshooting steps

If PojavLauncher is misbehaving or not working at all, you can try some self-repair before opening an issue or messaging the Discord.

**Restart the app.** Honestly, a simple restart will do in a lot of cases.

**Log in again.** If you've already logged in once and are having issues, swipe the account in question to the *left* and hit the Delete button. Log in with your account once more.

**Make sure you have the JDK installed.** PojavLauncher doesn't include the JDK, but Procursus and Doregon's Repository will automatically install it for you. If you manually installed PojavLauncher and don't have either of these repositories, you'll need to grab `openjdk-16-jre` from the Releases page.

**Can the JDK itself run?** Open a terminal or SSH connection and type `/usr/lib/jvm/java-16-openjdk/bin/java --version` into the window.

* If it returned **OpenJDK 16...**, then you're good.
* If it returned **Permission denied**, run `chmod -R +x /usr/lib/jvm/java-16-openjdk/bin/*` as root.
* If it returned **Killed: 9**, run `ldid -s /usr/lib/jvm/java-16-openjdk/bin/java`.
* If it returned **No such file or directory**, you need to install the JDK.

**Check file system permissions.** Open Filza and look for /var/mobile/Documents/minecraft and tap the info icon. If the user and group are not set to mobile, tap on mobile for each and make sure to select the "Apply to subitems" toggle at the bottom. Then check that the folder's permissions are

* User: Read, Write, Execute
* Group: Read, Write, Execute
* Others: Read

**Check file system storage.** Yeah, this can be an issue. Run an app like iCleaner before you try playing with critically low storage--however 100-200MB free should be good enough.

**Check the issues tab.** See anyone else with the same issue? Maybe an already closed one with a good answer? Checking out past issues can benefit greatly.

**Getting Cr4shed logs?** PojavLauncher has issues with older iOS devices that only have 1GB of memory, and can have issues with newer ones as well. These issues are explained on the [Making performance better](../going-further/performance) page.

**Reinstall PojavLauncher.** Possibly try using a different build as well. Doregon hosts multiple versions of PojavLauncher on his repository--if you installed `pojavlauncher`, try using `pojavlauncher-dev` instead.

**Respring or soft reboot.** Some files could have not been removed or installed properly, and sometimes respringing helps put them into their place. If it still doesn't work, try a userspace or soft reboot (you can find these options in PowerSelector).
