Arrowhead Framework OPC-UA service prosumer:
=======
OPC Variable Service
=======

## Introduction
This provided service from the OPC-UA service prosumer provides the information available from an OPC-UA enabled device.

## Service description
Provider will listen for incoming requests from Consumers wanting to read OPC-UA variables.
A Consumer can read an OPC-UA variable by making a HTTP GET request to the Provider sending it the OPC-UA endpoint, namespace, and variable it wishes to read.
These values are sent as URL parameters in the following way: 
```
GET opcVariable/{address}/{namespace}/{variableName}
```
Here "address" is the IP and port to the OPC-UA endpoint, "namespace" is the OPC-UA namespace one wishes to use, and "variableName" is the name of an variable within that namespace wrapped in double quotation marks (you might need to URL encode these using %22). An example of such an GET request to read the variable xBG5 in namespace 3 can be found below:
```
{providerIP:port}/opcVariable/10.48.134.10:4840/3/%22xBG5%22
```

When the Provider has received a request, it will first see if there is already an open connection to that endpoint.
If not it will connect to the endpoint and keep that connection until the Provider is shut down.
Then, it will read the requested variable and return its value, type and timestamp in a JSON format.

## Service registration
When the Provider is run, the first thing that it will do is to register itself with the Service Registry.
This is done by sending a "Service Registry Entry" to the Service Registry core service.
In more detail, this is achieved by sending a JSON object to URI:serviceregistry/register.
An example of such a Service Registry Entry is found below:
```
{
  "providedService" : {
    "serviceDefinition" : "OPCUARead",
    "interfaces" : [ "JSON" ],
    "serviceMetadata" : {
      "unit" : "unit"
    }
  },
  "provider" : {
"systemName" : "InsecureOPCUA2RESTProvider", "address" : "127.0.0.1",
"port" : 8460
  },
  "serviceUri" : "opcVariable",
  "version" : 1
}
```

## Service authorization
The second thing that the Provider does is that it adds a Consumer called "client1" that is allowed to consume the service IntraCloud.
This is done by sending an "IntraCloud Auth Entry" to the Authentication core service.
In more detail, this is achieved by sending a JSON object to URI: authorization/mgmt/intracloud.
An example of an IntraCloud Auth Entry can be found below:
```
{
  "consumer" : {
    "systemName" : "client1",
    "address" : "localhost",
    "port" : 8080
  },
  "providerList" : [ {
"systemName" : "InsecureOPCUA2RESTProvider", "address" : "127.0.0.1",
"port" : 8460
  } ],
  "serviceList" : [ {
    "serviceDefinition" : "OPCUARead",
    "interfaces" : [ "JSON" ],
    "serviceMetadata" : {
      "unit" : "unit"
    }
}] }
```

### Interface Design Description


___
Last updated: 2019.04.03 by [Jan van Deventer](mailto:jan.van.deventer@ltu.se).
