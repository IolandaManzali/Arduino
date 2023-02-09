---
title: Arduino IoT Cloud APIs
description: Arduino IoT Cloud has two different set of APIs. Read below to learn more
author: Karl Söderby, Fabrizio Mirabito
tags: [IoT Cloud, API, JavaScript]
---
The [Arduino IoT Cloud](https://create.arduino.cc/iot/) has different sets of APIs that provide different functionalities. This article serves as an introduction to how to work and what you can achieve with them.

## Configuration API
### What you can achieve
The main goal of Configuration API is to allow you to create and manage IoT resources like dashboards, devices, things, and variables, along with the retrieval and handling of historical data coming from your IoT Devices. The core of those APIs is organized around  [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer). Our API has predictable resource-oriented URLs, accepts  [form-encoded](https://en.wikipedia.org/wiki/POST_(HTTP)#Use_for_submitting_web_forms)  request bodies, returns  [JSON-encoded](http://www.json.org/) responses, and uses standard HTTP response codes, authentication, and verbs. You can use those APIs, both directly calling our HTTP endpoints or using our clients that wrap those calls into easy-to-use abstractions like objects and functions. We have Applications API clients available in `javascript`, `golang`, and `python`.

To use the Configuration API, you need to create an **API Key** in the [API Keys](https://cloud.arduino.cc/home/api-keys) section.

**Examples**

- Build an automated script to create your things, in bulk
- Duplicate the configuration of things, dashboards, devices
- Create your own personal web application to manage your resources
- Build a script that reads your variables' data and provides custom analytics 

You can find the full list of available resources and actions in the [Arduino IoT Cloud Configuration API Technical Reference](https://www.arduino.cc/reference/en/iot/api/).

## Data API
Data API allows sending and receiving any kind of data (sensors' values, commands for actuators, configuration changes...) from and to IoT Devices and the Cloud. Under the hood, they

- take care of the data exchange with our MQTT broker
- handle best in class authentication & security 
- manage compression, data format, and transport protocols

### What you can achieve
- Send sensors' values to the cloud
- Send and receive input and commands from and to dashboards
- Listen for variables' values changes and act upon them

Inside this set of API, we have:
	
- An official Arduino IoT Cloud Library for your Arduino sketches: `ArduinoIoTCloud.h` 
- An NPM Javascript package: `arduino-iot-js`  

**Arduino IoT Cloud Sketch library**
As described above, is the Arduino library that allows your Arduino devices to connect and exchange data with the IoT Cloud. If you edit your sketch directly inside IoT Cloud or Cloud Editor, you don't need to install it: it comes out of the box.

You can find more details at:

- The [official repository](https://github.com/arduino-libraries/ArduinoIoTCloud)
- The [cheat sheet](https://docs.arduino.cc/arduino-cloud/getting-started/technical-reference)

**Arduino IoT JS**
The `arduino-iot-js` NPM module is designed for communicating with the Arduino IoT Cloud broker using the MQTT over Websocket protocol. It is primarily used to send and receive variable values.

Example:

```js
const { ArduinoIoTCloud } = require('@arduino/arduino-iot-js');

ArduinoIoTCloud.connect(options)
  .then(() => {
    console.log("Connected to Arduino IoT Cloud");
    return ArduinoIoTCloud.onPropertyValue(thingId, variableName, showUpdates = value => console.log(value));
  })
  .then(() => console.log("Callback registered"))
  .catch(error => console.log(error));
```

Full examples and documentation can be found at:

- The [official repository](https://github.com/arduino/arduino-iot-js)
- The [NPM module](https://www.npmjs.com/package/arduino-iot-js) page  

## Backward Compatibility Policy

Public Arduino IoT Cloud APIs are exposing versioned endpoints and are committed to preserving compatibility with the following policies in place:
- When making a breaking change to the API signature or behavior, we will expose a new version of the endpoint.
- If we are making a change that is backward compatible with the existing version, we won't change the endpoint version.
- When introducing a new version of the API, we will preserve the previous version as deprecated for a reasonable amount of time to allow client migrations.
- We will not preserve multiple previous versions, just N-1 with respect to the current last released, hence upgrades are recommended.
- In any case, the frequency of version changes is expected to be less than once a year.
- It's also recommended that the client keeps the base URL of the API configurable because the base URL (currently api2.arduino.cc) might also change.