# Upsource PSI Agent with tools

This project contains a sample Dockerfile that declares an extended Upsource PSI Agent docker image with additional tools used for source code processing.

It is inherited from [jetbrains/upsource-psi-agent](https://hub.docker.com/r/jetbrains/upsource-psi-agent/) and contains the following tools:
- Node.js (latest LTS v6.x), 
- Yarn (latest stable)
- PHP (latest stable)
- Python 2.7.9 (part of the `openjdk:8` base image) with pip
- Python 3 (latest stable) with pip

For building the image you need to perform the following:

1. Choose [version](https://hub.docker.com/r/jetbrains/upsource-psi-agent/tags/) of base `jetbrains/upsource-psi-agent`
(referred to as `<version>` below)

2. `docker pull jetbrains/upsource-psi-agent:<version>`

3. Replace `@VERSION@` in Dockerfile with the `<version>` of [jetbrains/upsource-psi-agent](https://hub.docker.com/r/jetbrains/upsource-psi-agent/) base image you have chosen.

4. Run the docker build command:
`docker build -t upsource-psi-agent-with-tools:<version>`
