# Upsource PSI Agent with tools

This project contains a sample Dockerfile that declares an extended Upsource PSI Agent docker image with additional tools used for source code processing.

It is inherited from [jetbrains/upsource-psi-agent](https://hub.docker.com/r/jetbrains/upsource-psi-agent/) and contains the following tools:
- Node.js (latest LTS v6.x), 
- Yarn (latest stable)
- PHP (latest stable)
- Python 2.7.9 (part of the `openjdk:8` base image) 
- Python 3 (latest stable) with pip
- Android SDK Tools 25.2.5 + SDK platform 26 +  SDK build tools 26

For building the image you need to perform the following:

1. Choose [version](https://hub.docker.com/r/jetbrains/upsource-psi-agent/tags/) of base `jetbrains/upsource-psi-agent`
(referred to as `<version>` below)

2. `docker pull jetbrains/upsource-psi-agent:<version>`

3. Replace `@VERSION@` in Dockerfile with the `<version>` of [jetbrains/upsource-psi-agent](https://hub.docker.com/r/jetbrains/upsource-psi-agent/) base image you have chosen.

4. For Upsource instance hosting Android projects, Android SDK might be installed. For that:
- copy all the files from $ANDROID_HOME/licenses folder located on your developer machine to the folder android-licenses of docker build context (see details on Android SDK licensing scheme: <link-to-the Android site>).
- add installation lines in Dockerfile for every Android SDK platform and build tools supported in you projects (Android 2.6 is added as an example there)
  
   OR remove all Android related lines from Dockerfile if your projects have nothing to do with Android.

5. Run the docker build command:
`docker build -t upsource-psi-agent-with-tools:<version>`
