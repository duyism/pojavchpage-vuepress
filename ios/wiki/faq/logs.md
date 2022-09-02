# Where can I find logs?

* For the PojavLauncher-created log, find `/var/mobile/Documents/.pojavlauncher/latestlog.txt`. This will only be created if the JVM was able to start.

* For the JVM-created log, find `/var/mobile/Documents/minecraft/hs_err_pidXXXX.log`. This one will only be created if there's an issue with the JVM.

* For CrashReporter logs, you can use Cr4shed to get them (available for free on Packix). Common issues include `0x68 is not a valid region` or `The process was terminated for exceeding jetsam memory limits.` 
