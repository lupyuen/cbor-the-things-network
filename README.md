# The Things Network Payload Formatter for Concise Binary Object Representation (CBOR)

Copy and paste [`cbor.js`](cbor.js) into the JavaScript Payload Formatter for The Things Network.

We shall use the CBOR Payload Formatter to ingest CBOR Sensor Data (MQTT) into Prometheus...

https://github.com/hikhvar/mqtt2prometheus

More about The Things Network Payload Formatters...

https://www.thethingsindustries.com/docs/integrations/payload-formatters/javascript/

Helium also supports Payload Formatters...

https://docs.helium.com/use-the-network/console/functions/

This CBOR Payload Formatter is based on...

https://github.com/paroga/cbor-js

# MQTT Log

This MQTT command...

```bash
## Change au1.cloud.thethings.network to our MQTT Public Address
## Change luppy-application@ttn to our MQTT Username
mosquitto_sub -h au1.cloud.thethings.network -t "#" -u "luppy-application@ttn" -P "YOUR_API_KEY" -d
```

Shows this MQTT Message containing the Decoded Payload...

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

This Storage API command...

```bash
## Change au1.cloud.thethings.network to our Storage API Public Address
## Change $YOUR_APPLICATION_ID to our Application ID
## Change $YOUR_API_KEY to our API Key
curl \
  -G "https://au1.cloud.thethings.network/api/v3/as/applications/$YOUR_APPLICATION_ID/packages/storage/uplink_message" \
  -H "Authorization: Bearer $YOUR_API_KEY" \
  -H "Accept: text/event-stream" \
  -d "limit=1" \
  -d "order=-received_at"
```

Shows this Stored Message containing the Decoded Payload...

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
