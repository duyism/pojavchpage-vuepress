# Getting PojavLauncher with Doregon's Repo

#### If you're using unc0ver, checkra1n, or another jailbreak with Substitute/Substrate, or wish to get a newer package on the Procursus bootstrap, this one's for you.

**NOTE:** Using Doregon's Repo on Procursus has some small oddities--when viewing a package that's on Doregon's Repo *and* Procursus, you'll see the information and download the package from Procursus. This applies to `pojavlauncher` and `openjdk-16-jre`.

Doregon has taken the liberty to host PojavLauncher on his repository for those without Procursus or those looking for a rolling release build. To get started with his copies, follow the simple steps:

1. Open a package manager of your choice.
2. Add `https://apt.doregon.gq/` to your sources list.
3. Search for `pojavlauncher`.
4. Download and install the package depending on your preference:
    * `pojavlauncher` installs the latest stable build--meaning the latest release on the GitHub repository. This one's good for making sure you're not going to get updates every time a new commit is pushed, or you want the stability because there isn't a chance of the game dying with every update.
    * `pojavlauncher-dev` installs the latest successful commit--meaning that you're getting the latest features and code-changes. This one's good if you want to test out and help the developers work out bugs and kinks, but has the chance of being unstable and buggy at times. It also updates regularly, so make sure you visit his repo and check for a new update from time to time. (It also includes Zink now!)
    * ~~`pojavlauncher-zink`~~ Zink renderer has been merged to `pojavlauncher-dev`.

Everything will be installed for you. The dependency--**openjdk-8-jre**--simply includes the Java 8 package, required to run Minecraft. You can also install openjdk-16-jre to have support for 1.17, and openjdk-17-jre (Procursus only) for newer 1.18 snapshots.
