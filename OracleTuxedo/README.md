Oracle Tuxedo on Docker
===============
Sample Docker configurations to facilitate installation, configuration, and environment setup for DevOps users. This project includes [dockerfiles](dockerfiles/) and [samples](samples/) for Tuxedo 12.1.3 and 12.2.2 based on Oracle Linux.

The certification of Tuxedo on Docker does not require the use of any file presented in this repository. Customers and users are welcome to use them as starters, and customize/tweak, or create from scratch new scripts and Dockerfiles.

## How to build and run
This folder contains the information and examples of how to use [Tuxedo](http://oracle.com/tuxedo) with [Docker](https://www.docker.com/).

To assist in building the images, you can use the [buildDockerImage.sh](dockerfiles/buildDockerImage.sh) script. See below for instructions and usage.

The `buildDockerImage.sh` script is just a utility shell script that performs MD5 checks and is an easy way for beginners to get started. Expert users are welcome to directly call `docker build` with their prefered set of parameters.

## To use
> Note: Tuxedo 12.2.2 Docker image depends on the `oracle/serverjre:8` image. You must first download the Oracle Server JRE binary and drop in folder `../OracleJava/java-8` and build that image. For more information, visit the [OracleJava](../OracleJava) folder's [README](../OracleJava/README.md) file.

1. Into an empty directory:
  * Download all the files from this github directory
  * Download the Tuxedo 12.2.2 or 12.1.3 Linux 64 bit installer from OTN. For more information about the installer file names and download location, refer to the corresponding `Dockerfile` in the `dockerfiles/<version>` folder.
  * Optionally download the latest Tuxedo rolling patch from My Oracle Support
2. cd dockerfiles
3. Execute the 'buildDockerImage.sh' to build:

```bash
$ bash ./buildDockerImage.sh -h
Usage: buildDockerImage.sh [-hs] -v version -i installer [-m md5value]
Builds a Docker Image for Oracle Tuxedo.
  
Parameters:
   -h: Help
   -v: Version to build. Required.
       Choose one of: 12.1.3  12.2.2  
   -s: Skips the MD5 check of packages.
   -i: Installer name. Required.
   -m: MD5 value expected. Required if -s not specified.
LICENSE CDDL 1.0 + GPL 2.0

Copyright (c) 2016-2016 Oracle and/or its affiliates. All rights reserved.
```

You should end up with a docker image tagged oracle/tuxedo:version

You can then start the image in a new container with:  `docker run -i -t oracle/tuxedo:version /bin/bash`
which will put you into the container with a bash prompt.  If you want to test the new container, simply execute the `simpapp_runme.sh` in an empty
directory and the script will build and run the Tuxedo simpapp application.


 * Tuxedo Distribution and Documentation
   - For more information on the Tuxedo 12cR2 Distribution, visit [Tuxedo Installer OTN download page](http://www.oracle.com/technetwork/middleware/tuxedo/downloads/index.html).

   - For more information on the Tuxedo 12cR2 Documentation, visit [Tuxedo 12.2.2 Documentation](http://docs.oracle.com/cd/E72452_01/tuxedo/index.html).

## Oracle TSAM Plus on Docker
For more information about TSAM Plus Docker image, refer to [README](OracleTSAM/README.md) in [OracleTSAM](OracleTSAM/) folder.

## License
To download and run Tuxedo 12cR2 regardless of inside or outside a Docker container, you must download the binaries from Oracle website and accept the license indicated at that page.

All scripts and files hosted in this project and GitHub [docker/OracleTuxedo](./) repository required to build the Docker images are, unless otherwise noted, released under the Common Development and Distribution License (CDDL) 1.0 and GNU Public License 2.0 licenses.

## Copyright
Copyright (c) 2016-2016 Oracle and/or its affiliates. All rights reserved.


