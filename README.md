Arrowhead Framework OPC-UA service prosumer:
=======
Prosumer Description
=======

Service prosumer version: 0.2 compatible with the [Arrowhead Framework 4.x](https://github.com/arrowhead-f).

## Introduction
The Arrowhead Framework OPC-UA service prosumer is a (Java) program that allows other Arrowhead Prosumers to connect to OPC-UA endpoints (e.g. a PLC) and read variables from them. It can be seen as a wrapper that enables the OPC-UA device to offer services within a local cloud.

## Services
Being an Arrowhead Framework service prosumer, it produces and consumes services of other prosumers within its local cloud.

### Produced services
- [opcVariable](opcVariable.md)

### Consumed services
The prosumer consumes the necessary services of the core prosumers within its local cloud, such as:
- [Orchestration](https://github.com/arrowhead-f/core-java/tree/master/documentation/Orchestrator)

=======

## Installation
This prosumer is a [Maven](http://maven.apache.org/) module. To build and run this prosumer, use the following steps.

### Configure
NOTE! There are no OPC-UA configurations available in this file yet. 

### Build
Build the module using [Maven](http://maven.apache.org/).

### Run
To **start** the service prosumer, run: `java -jar provider-4.0.jar -auth` after building the Maven module. 
The `-auth` flag is optional and only adds the example Consumer found in the "tester" folder to the IntraCloud authorization so that it is allowed to consume the service.

### Shutdown
To **stop** the prosumer, type `stop` in the Terminal window in which it was started.

## Prosumer design
This prosumer is not proprietary.
Its design description can be found in the file: [prosumerDesignDescription.md](prosumerDesignDescription.md)
