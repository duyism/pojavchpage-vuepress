# Environment variables

PojavLauncher uses many environment variables (don’t confuse with JVM arguments!) to configure the game. You can specify some of them by typing the keys on a file called `custom_env.txt` (in /var/mobile/Documents/.pojavlauncher), with a line break after each key.

### Some basic environment variables

~~`GL4ES_LIBNAME`~~ `RENDERER`: Set the renderer you wish to use.

~~Example: `GL4ES_LIBNAME=libgl4es_115.dylib`~~ (this key is being integrated to the launcher preferences)

`JAVA_HOME`: Set the Java directory.

~~Example: `JAVA_HOME=/usr/lib/jvm/java-16-openjdk`~~ (this key is also being integrated to the launcher preferences)

`LIBGL_GL`: Set the output OpenGL. (It can not be used to launch 1.17 or later without the fix!)

Example: `LIBGL_GL=32

There are more keys related to gl4es. You can read all of them at [this website.](https://github.com/PojavLauncherTeam/gl4es/blob/master/USAGE.md)

