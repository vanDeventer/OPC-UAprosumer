Arrowhead Framework OPC-UA service prosumer:
=======
OPC Variable Service
=======

## Introduction
This provided service from the [OPC-UA](https://github.com/nenovrak/OPC-UAprosumer/blob/master/OPC%20Unified%20Architecture.pdf) service prosumer provides the information available from an OPC-UA enabled device.

## Service description
Provider will listen for incoming requests from Consumers wanting to read OPC-UA variables.
A Consumer can read an OPC-UA variable by making a HTTP GET request to the Provider sending it the OPC-UA endpoint, namespace, and variable it wishes to read.
These values are sent as URL parameters in the following way: 
```
HTTP GET {prosumerIP:port}/opcVariable/{OPC-UA_endpointIP:port}/{namespace}/{variableName}
```
Here *OPC-UA_endpointIP:port* is the IP and port to the [OPC-UA](https://github.com/nenovrak/OPC-UAprosumer/blob/master/OPC%20Unified%20Architecture.pdf) endpoint, *namespace* refers to the OPC-UA namespace one wishes to use, and *variableName* is the name of an variable within that namespace wrapped in double quotation marks (you might need to URL encode these using %22). An example of such an GET request to read the variable *xBG5* in namespace *3* can be found below:
```
HTTP GET {providerIP:port}/opcVariable/10.48.134.10:4840/3/%22xBG5%22
```

When the Provider has received a request, it will first assess whether there is already an open connection to that endpoint.
If not it will connect to the endpoint and keep that connection until the Provider is shut down.
Then, it will read the requested variable and return its value, type and timestamp in a JSON format. An example output from the service is found below:

```
{
  Example output goes here...
}
```
