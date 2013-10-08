
Android-based Code Offload Converter: A Demo Example
====================================================================

This demo example shows how the [converter](https://github.com/huberflores/CodeOffloadingAnnotations) transforms the methods of an Android application into offlodable components.


Requirements
--------------------
1. A linux server x86 
2. Dalvik VM libraries installed and configured in a file named “rund.sh”, described here:
https://github.com/alirezaostovar/codeoffloading/blob/master/rund.sh

Requirements (Maven build)
--------------------------
The example consists of two parts, one for client and the other for server. The server application can be built by running the following maven commands within the application's root directory.

```xml
mvn clean package
mvn install
```

Then the produced apk file must be placed next to the configured rund 
file above. This apk can be run on android VM using following fixed command:

```xml
./rund.sh -cp projectname.apk MC.NetClasses.Main
```

Before opening and compiling the client part and producing apk file, the server IP must be set.
This can be done with setting the variable called IPAddress in the file “NetInfo.java” 
inside MC package. The client application can be built and deployed to the connected device by running the following maven commands within the application's root directory.

```xml
mvn clean package
mvn install
mvn android:deploy
```

It should be noted that, as the variable IPAddress is a byte array, if the server IP 
contains numbers more than 127, this number must be presented as a negative number using 
Two’s Complement system. For example, for the number 255, it will be -1.

Each application has two buttons, one for running the test locally and the other one for 
running on the cloud. It is better to execute the tests separately, for example first 
locally, then on cloud. Depending on the resource-intensiveness of each test, it might 
take several seconds or even minutes to be executed. For running the test on the cloud, 
the server version must be running on the cloud before pressing the designated button. 
This was described above.

