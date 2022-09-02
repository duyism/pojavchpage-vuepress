# Custom Java arguments

If you were using Java arguments that optimize garbage collection or increase the memory, you can still use them in PojavLauncher by writing them to a file called `overrideargs.txt`.

## Before writing the file

An update to PojavLauncher changed where it looked for the arguments file. If you're using on of the below versions, you'll need to substitute `/var/mobile/Documents/.pojavlauncher/` with `/var/mobile/Documents/minecraft`.

* Any GitHub Actions build from *before* commit [`19cbac0`](https://github.com/PojavLauncherTeam/PojavLauncher_iOS/commit/19cbac05b1a0eb17fc6eff57753df2e316c04cdd) (before March 17, 2021).
* Any version from the Releases page.
* Any version from Procursus *before* April 19, 2021.
* Any version of `pojavlauncher` from Doregon's Repository *before* April 19, 2021.

## Setting your own arguments

First, create the `/var/mobile/Documents/.pojavlauncher/overrideargs.txt` file. Now you can get to messing with Java arguments. The way you enter them is with a dash and then the argument:

`-Xmx3G`

**Not all arguments will work with PojavLauncher.** This was brought to our attention on May 18, after someone tried using a set of arguments from the FeedTheBeast subreddit. Here's a set that reduces lag spikes (from the Android repository)
```
-XX:+DisableExplicitGC -XX:+UseNUMA -XX:MaxTenuringThreshold=15 -XX:MaxGCPauseMillis=30 -XX:GCPauseIntervalMillis=150 -XX:-UseGCOverheadLimit -XX:+UseBiasedLocking -XX:SurvivorRatio=8 -XX:TargetSurvivorRatio=90 -XX:MaxTenuringThreshold=15 -Dfml.ignorePatchDiscrepancies=true -Dfml.ignoreInvalidMinecraftCertificates=true -XX:+UseCompressedOops -XX:+OptimizeStringConcat -XX:ReservedCodeCacheSize=2048m -XX:+UseCodeCacheFlushing -XX:SoftRefLRUPolicyMSPerMB=2000 -XX:ParallelGCThreads=10
```
If `latestlog.txt` has a line said `An error occurred during the VM initialization` and you're sure that the permissions for your files are correct, your arguments will not work.

## `-Xms` and `-Xmx`

By default, PojavLauncher changes the `-Xms` and `-Xmx` values based on what iOS device is being used, to 25% of total RAM amount. The currently known values are at the bottom of this page.

To set the *minimum* memory that PojavLauncher can use, add the `-Xms` argument. This one accepts a number **with a suffix** of K (for kilobytes), M (for megabytes), or G (for gigabytes). We recommend using the M suffix to prevent issues with too little or too much memory. This argument requires the presence of the next argument to function correctly, and cannot be greater than it. An example is `-Xms1024M`, which means that when the game starts, it will allocate 1024 megabytes of memory.

To set the *maximum* memory that PojavLauncher can use, add the `-Xmx` argument. This one accepts a number **with a suffix** of K (for kilobytes), M (for megabytes), or G (for gigabytes). We recommend using the M suffix to prevent issues with too little or too much memory. This argument requires the presence of the previous argument to function correctly, and cannot be less than it. An example is `-Xmx1024M`, which means that when the game starts, it will be able to use up to 1024 megabytes of memory.

The tables below show what values PojavLauncher sets as the maximum memory that it can use. You can choose to go farther than these values with the `-Xmx` argument, but be warned that iOS may kill the game more frequently (a workaround is explained on [this page](overb0arding)). We recommend keeping the `-Xms` value below the values listed here, because then the game may crash when starting.

### Table of devices and memory allocation

All values are estimates. The real values will be slightly lower. The latest iOS versions are here for reference.

#### iPhone

| iPhone model  | Memory Allocation | Latest iOS |
| ------------- | ------------- | ------------- |
| iPhone 5s, iPhone 6/6 Plus | 256 megabytes | iOS 12.5.4 |
| iPhone 6s/6s Plus, iPhone SE (1st generation), iPhone 7, iPhone 8  | 512 megabytes | current |
| iPhone 7 Plus, iPhone 8 Plus, iPhone X, iPhone XR, iPhone SE (2nd generation) | 768 megabytes | current | 
| iPhone XS/XS Max, iPhone 11/11 Pro/11 Pro Max | 1024 megabytes | current | 
| iPhone 12 mini/12/12 Pro/12 Pro Max | 1536 megabytes | current | 

#### iPad

**Note:** The iPad Pro 11" 1st gen and 12.9" 2nd gen can have either 4GB or 6GB of total memory. If your model has 1TB of storage, you will have 6GB. If not, you will have 4GB. The same concept applies to the iPad Pro 11” 3rd gen and 12.9” 5th gen: if your model has 1TB or higher, you have 16GB of total memory. If not, you have 8GB. 

| iPad model  | Memory Allocation | Latest iOS/iPadOS | 
| ------------- | ------------- | -----------------|
| iPad Air, iPad mini 2, iPad mini 3 | 256 megabytes  | iOS 12.5.4 |
| iPad Air 2, iPad mini 4, iPad (5th generation), iPad Pro 9.7” | 512 megabytes | current |
| iPad Air 3, iPad mini 5, iPad (6th to 8th generation) | 768 megabytes | current | 
| iPad Air 4, iPad Pro 10.5”, iPad Pro 12.9” (1st and 2nd generation) | 1024 megabytes | current | 
| iPad Pro 11" 1st generation, iPad Pro 12.9” 3rd generation | 1024 or 1536 megabytes | current | 
| iPad Pro 11" 2nd generation, iPad Pro 12.9” 4th generation | 1536 megabytes | current | 
| iPad Pro 11” 3rd generation, iPad Pro 12.9” 5th generation | 2048 or 4096 megabytes | current | 

#### iPod

| iPod model  | Memory Allocation | Latest iOS |
| ------------- | ------------- | ------------- |
| iPod touch 6 | 256 megabytes | iOS 12.5.4 |
| iPod touch 7 | 512 megabytes | current |
