# The Things Network Payload Formatter for Concise Binary Object Representation (CBOR)

See [`cbor.js`](cbor.js)

# MQTT Log

```json
{
    "end_device_ids": {
        "device_id": "eui-YOUR_DEVICE_EUI",
        "application_ids": {
            "application_id": "luppy-application"
        },
        "dev_eui": "YOUR_DEVICE_EUI",
        "join_eui": "0000000000000000",
        "dev_addr": "YOUR_DEVICE_ADDR"
    },
    "correlation_ids": [
        "as:up:01FHW2DT9KWHND8J14NC0MV40W",
        "gs:conn:01FH9PV9YH5J0V5R3RQ9FDNXSH",
        "gs:up:host:01FH9PVA6TJQTJ0CP5GCXYS4S2",
        "gs:uplink:01FHW2DT34PYCK248PA3D6QT1S",
        "ns:uplink:01FHW2DT35MFV6VXFYNWPJD2YR",
        "rpc:/ttn.lorawan.v3.GsNs/HandleUplink:01FHW2DT354AP6BE2PY0V7DCAS",
        "rpc:/ttn.lorawan.v3.NsAs/HandleUplink:01FHW2DT9JKWRYNSVD110XQWBC"
    ],
    "received_at": "2021-10-13T05:36:28.468873930Z",
    "uplink_message": {
        "session_key_id": "YOUR_SESSION_KEY_ID",
        "f_port": 2,
        "f_cnt": 14,
        "frm_payload": "omF0GRIwYWwZD6A=",
        "decoded_payload": {
            "l": 4000,
            "t": 4656
        },
        "rx_metadata": [
            {
                "gateway_ids": {
                    "gateway_id": "YOUR_GATEWAY_ID",
                    "eui": "YOUR_GATEWAY_EUI"
                },
                "time": "2021-10-13T06:14:28.908371Z",
                "timestamp": 1855659042,
                "rssi": -55,
                "channel_rssi": -55,
                "snr": 12.8,
                "location": {
                    "latitude": 1.27125,
                    "longitude": 103.80795,
                    "altitude": 70,
                    "source": "SOURCE_REGISTRY"
                },
                "uplink_token": "YOUR_UPLINK_TOKEN",
                "channel_index": 1
            }
        ],
        "settings": {
            "data_rate": {
                "lora": {
                    "bandwidth": 125000,
                    "spreading_factor": 10
                }
            },
            "data_rate_index": 2,
            "coding_rate": "4/5",
            "frequency": "923400000",
            "timestamp": 1855659042,
            "time": "2021-10-13T06:14:28.908371Z"
        },
        "received_at": "2021-10-13T05:36:28.261985742Z",
        "consumed_airtime": "0.370688s",
        "network_ids": {
            "net_id": "000013",
            "tenant_id": "ttn",
            "cluster_id": "ttn-au1"
        }
    }
}
```

# Storage Log

```json
{
    "result": {
        "end_device_ids": {
            "device_id": "eui-YOUR_DEVICE_EUI",
            "application_ids": {
                "application_id": "luppy-application"
            },
            "dev_eui": "YOUR_DEVICE_EUI",
            "dev_addr": "YOUR_DEVICE_ADDR"
        },
        "received_at": "2021-10-13T05:36:28.468873930Z",
        "uplink_message": {
            "f_port": 2,
            "f_cnt": 14,
            "frm_payload": "omF0GRIwYWwZD6A=",
            "decoded_payload": {
                "l": 4000,
                "t": 4656
            },
            "rx_metadata": [
                {
                    "gateway_ids": {
                        "gateway_id": "YOUR_GATEWAY_ID",
                        "eui": "YOUR_GATEWAY_EUI"
                    },
                    "time": "2021-10-13T06:14:28.908371Z",
                    "timestamp": 1855659042,
                    "rssi": -55,
                    "channel_rssi": -55,
                    "snr": 12.8,
                    "location": {
                        "latitude": 1.27125,
                        "longitude": 103.80795,
                        "altitude": 70,
                        "source": "SOURCE_REGISTRY"
                    },
                    "channel_index": 1
                }
            ],
            "settings": {
                "data_rate": {
                    "lora": {
                        "bandwidth": 125000,
                        "spreading_factor": 10
                    }
                },
                "data_rate_index": 2,
                "coding_rate": "4/5",
                "frequency": "923400000",
                "timestamp": 1855659042,
                "time": "2021-10-13T06:14:28.908371Z"
            },
            "received_at": "2021-10-13T05:36:28.261985742Z",
            "consumed_airtime": "0.370688s",
            "network_ids": {
                "net_id": "000013",
                "tenant_id": "ttn",
                "cluster_id": "ttn-au1"
            }
        }
    }
}
```

cbor-js
=======

The Concise Binary Object Representation (CBOR) data format ([RFC 7049](http://tools.ietf.org/html/rfc7049)) implemented in pure JavaScript.

[![Build Status](https://api.travis-ci.org/paroga/cbor-js.svg)](https://travis-ci.org/paroga/cbor-js)
[![Coverage Status](https://coveralls.io/repos/paroga/cbor-js/badge.svg?branch=master)](https://coveralls.io/r/paroga/cbor-js?branch=master)
[![Dependency status](https://david-dm.org/paroga/cbor-js/status.svg)](https://david-dm.org/paroga/cbor-js#info=dependencies&view=table)
[![Dev Dependency Status](https://david-dm.org/paroga/cbor-js/dev-status.svg)](https://david-dm.org/paroga/cbor-js#info=devDependencies&view=table)
[![Selenium Test Status](https://saucelabs.com/buildstatus/paroga-cbor-js)](https://saucelabs.com/u/paroga-cbor-js)

[![Selenium Test Status](https://saucelabs.com/browser-matrix/paroga-cbor-js.svg)](https://saucelabs.com/u/paroga-cbor-js)

API
---

The `CBOR`-object provides the following two functions:

CBOR.**decode**(*data*)
> Take the ArrayBuffer object *data* and return it decoded as a JavaScript object.

CBOR.**encode**(*data*)
> Take the JavaScript object *data* and return it encoded as a ArrayBuffer object.

Usage
-----

Include `cbor.js` in your or HTML page:
```html
<script src="path/to/cbor.js" type="text/javascript"></script>
```

Then you can use it via the `CBOR`-object in your code:
```javascript
var initial = { Hello: "World" };
var encoded = CBOR.encode(initial);
var decoded = CBOR.decode(encoded);
```
After running this example `initial` and `decoded` represent the same value.

### Combination with WebSocket

The API was designed to play well with the `WebSocket` object in the browser:
```javascript
var websocket = new WebSocket(url);
websocket.binaryType = "arraybuffer";
...
websocket.onmessage = function(event) {
  var message = CBOR.decode(event.data);
};
...
websocket.send(CBOR.encode(message));
```
