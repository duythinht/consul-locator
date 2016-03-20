# consul-locator

This is consul wrapper for discovery and detect a service changed.

Usage:

### serviceFor

Initialize a new Service wrapper
  
    var Service = require('consul-locator').serviceFor(options)

Options

* host (String, default: 127.0.0.1): agent address
* port (String, default: 8500): agent HTTP(S) port
* secure (Boolean, default: false): enable HTTPS
* ca (String[], optional): array of strings or Buffers of trusted certificates in PEM format
* defaults (Object, optional): default options for method calls
* promisify (Boolean|Function, optional): convert callback methods to promises


### Service(serviceName)

Discovery a service

    var service = new Service('hello-world')

Methods:
* watch: Listen to service changed
* subscribe: subscribe to a key and listen to key changed

#### watch(callback)

    sevice.watch((data) => {
        //Do with changed data
        console.log(data)
    })

#### subscribe(key, callback)

    service.subscribe('hello/tcp/port', (value) => {
      // Do something with changed value of key `hello/tcp/port`
      console.log(`tcp port has been changed to ${value}`)
    });
