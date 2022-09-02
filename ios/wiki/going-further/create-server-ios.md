# Create a Minecraft server

Although PojavLauncher is mainly client-side, you still can launch a server with it!

Currently, PojavLauncher iOS supports servers up to the latest Minecraft version. (Requires Java 16)

# How to launch a Minecraft server using terminal

Before doing all the steps below, make sure you installed a terminal.

### Step 1: Download the server launcher

You can use PaperMC for the best experience. Download it [here](https://papermc.io/downloads).

### Step 2: Launch Paper for the first time

Type these commands:
`cd /var/mobile/Documents/minecraft/`

`/usr/lib/jvm/java-16-openjdk/bin/java -jar <path_to_file>`

With:

`<path_to_file>` is the path to the downloaded jar.

Pro tips:

- Put the Paper jar file to `var/mobile/Documents/minecraft` for better access. After doing that, you can just type the name of the file for `<path_to_file>`.

- Create a symbolic link for `/usr/lib/jvm/java-16-openjdk/bin/java` as `java`.

### Step 3: Before running the server...

After the first launch, you need to accept the EULA. Go to /var/mobile/Documents/minecraft and edit the eula.txt file as follows:
`<something_here>
eula=true`

### Step 4: Run the server

Before launching the server, you can configure how the server runs.

First, go to `/var/mobile/Documents/minecraft/server.properties`. There are many options for you to configure, like the server port, game mode, height limit for building, ... 

After that, type these commands to start the server (type `java` instead of `/usr/lib/jvm/java-16-openjdk/bin/java` if you created the symbolic link as above):

`cd /var/mobile/Documents/minecraft`

`/usr/lib/jvm/java-16-openjdk/bin/java -Xmx<a_number>[<suffix>] -Xms<another_number>[<suffix>] -jar <path_to_file> --nogui`

With:

`[<suffix>]` can be (nothing) for bytes, `K` for kilobytes, `M` for megabytes, `G` for gigabytes.

`<path_to_file>` is the path to the downloaded jar for Paper.

Example:

`java -jar /var/mobile/Documents/paper-1.17.1-165.jar -Xms1G -Xmx1G --nogui`

The server will be launched after some time.

**You have read all the steps! Now just enjoy the created server!**

To shut down the server, simply type `stop` or run this command:

`sudo killall -9 java`

### Known issues with this method

- May cause a respring loop if a server is created and after that, there is too little memory left. If you experience this issue, you can reboot the device, or SSH to your device and run the `killall` command.

- If the terminal process is terminated, the server will be unable to access. A workaround is described below.

- Connecting from an Android phone (or maybe an iOS phone as well) causes crash on the client. (This issue is being tested and investigated.)

# Other methods

- The ability to run Paper on the new mod installer is being tested. An instruction will be made if the tests are successful.

# Going further

- Want to get rid of the terminal? Try setting an Activator (currently broken on iOS 14) action that launch a server with this command:

`cd /var/mobile/Documents/minecraft && java -jar [<some_jvm_arguments>] paper-<version>.jar`

**This is the only known way to prevent crash issue as said above.**

- You can create and run multiple servers at one time! To do this, you need to modify (at least) the `server-port` and `level-name` keys in `server.properties`. Then simply redo step 4.
