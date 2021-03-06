tessel-edge
===========

Edge software for the [reelyActive](https://www.reelyactive.com) __Owl-in-One__ based on the [Tessel 2](https://tessel.io/) platform.  Forwards [raddecs](https://github.com/reelyactive/raddec/) from a reel module (BLE) and/or from tcpdump (WiFi).


Installation
------------

Clone this repository, browse to its root, then run:

    npm install


Configuration
-------------

All configuration parameters can be found in the file __config.js__.  Update only this file, as required.

| Parameter         | Description                                            | 
|:------------------|:-------------------------------------------------------|
| RADDEC_TARGETS    | Array of targets for raddec data (see below)           |
| LISTEN_TO_REEL    | Enable listener on reel module (default: true)         |
| LISTEN_TO_TCPDUMP | Enable listener on tcpdump (default: false)            |
| ENABLE_MIXING     | Combine multiple decodings of an individual transmitter into a single raddec (default: true) |
| INCLUDE_TIMESTAMP | Include the optional timestamp in each raddec (default: true) |
| INCLUDE_PACKETS   | Include the optional packets in each raddec (default: true) |

Each raddec target in the RADDEC_TARGETS array is an object with the following properties:
- _host_: an IP address or hostname (ex: '192.168.0.100')
- _port_: the target port (default: 50001)
- _protocol_: the transport protocol, either 'udp' or 'webhook' (HTTP POST)
- _options_: in the case of a 'webhook' the defaults are { useHttps: false, path: '/raddecs' }, which can be overridden


Programming
-----------

Programming the Tessel 2 requires the [t2-cli](https://www.npmjs.com/package/t2-cli) package which can be installed by following [these instructions](http://tessel.github.io/t2-start/).

With the Tessel 2 connected to the programming station via USB, from the root of this repository run:

    t2 push index.js

The code will be pushed to flash memory on the Tessel and will run every time it boots.


Prerequisites
-------------

The __tessel-edge__ software expects the following:
- a reel or reelceiver module connected via UART on Port A
- maximum baud rate of Port A set to at least 230400
- tcpdump installed


License
-------

MIT License

Copyright (c) 2018-2019 [reelyActive](https://www.reelyactive.com)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR 
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, 
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE 
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER 
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, 
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN 
THE SOFTWARE.
