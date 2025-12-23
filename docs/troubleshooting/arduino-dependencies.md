# Resolving missing Arduino library headers

When compiling Arduino sketches that depend on external libraries, the build will fail if the
library has not been installed in the Arduino environment. A common example is the `PubSubClient`
MQTT client. Compilation stops with an error similar to the following:

```
fatal error: PubSubClient.h: No such file or directory
```

To resolve the problem:

1. Open the Arduino IDE and navigate to **Sketch → Include Library → Manage Libraries…**
2. Use the Library Manager search bar to look up **PubSubClient** by Nick O'Leary.
3. Install the latest stable release of the library.
4. Rebuild the sketch. The IDE will now locate `PubSubClient.h` automatically.

If you are building outside of the Arduino IDE (for example, using `arduino-cli` or another
continuous-integration workflow) you can install the dependency manually by cloning the library
into your sketchbook `libraries` directory:

```
cd <your-sketchbook>/libraries
git clone https://github.com/knolleary/pubsubclient.git PubSubClient
```

After the library has been added to your environment, re-run the build to verify that the error is
cleared. The header file will now be available to any sketch that includes `<PubSubClient.h>`.
