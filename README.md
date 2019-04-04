Arrowhead Framework OPC-UA service prosumer:
=======
Prosumer Description
=======

Service prosumer version: 0.2 compatible with the [Arrowhead Framework 4.x] (https://github.com/arrowhead-f).

## Introduction
The Arrowhead Framework OPC-UA service prosumer is a (Java) program that allows other Arrowhead Prosumers to connect to OPC-UA endpoints (e.g. a PLC) and read variables from them. It can be seen as a wrapper that enables the OPC-UA device to offer services within a local cloud.

## Services
Being an Arrowhead Framework service prosumer, it produces and consumes services of other prosumers within its local cloud.

### Produced services
- [opcVariable](opcVariable.md)

### Consumed services
The prosumer consumes the necessary services of the core prosumers within its local cloud, such as:
- [Orchestration](https://github.com/arrowhead-f/core-java/tree/master/documentation/Orchestrator)

## Basic operations
To **start** the service prosumer, run: `java -jar provider-4.0.jar -auth` after building the Maven module. 
The `-auth` flag is optional and only adds the Consumer found in the "tester" folder to the IntraCloud authorization so that it is allowed to consume the service.

To **stop** the prosumer, type `stop` in the Terminal window in which it was started.

### Configuration file
Where is it and what does it do?
Should that have its own description document?

## Prosumer design
This prosumer is not proprietary.
Its design description can be found in the file: [prosumerDesignDescription.md](prosumerDesignDescription.md)
