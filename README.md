# IoT2021HW1

First individual assignment of iot course

---

### Setting up the broker

In general, any MQTT-SN capable broker or broker/gateway setup will do.
These are the steps to follow to setup the Mosquitto Real Simple Message Broker:

1. Get the RSMB here: https://github.com/eclipse/mosquitto.rsmb

```
git clone https://github.com/eclipse/mosquitto.rsmb.git
```

2. Go into the source folder and build the RSMB

```
cd mosquitto.rsmb/rsmb/src
make
```

3. Create a config file. In this case we run the RSMB as MQTT and MQTT-SN
   capable broker, using port 1885 for MQTT-SN and 1886 for MQTT and enabling
   IPv6, so save the following to `config.conf`:

```
# add some debug output
trace_output protocol

# listen for MQTT-SN traffic on UDP port 1885
listener 1885 INADDR_ANY mqtts
  ipv6 true

# listen to MQTT connections on tcp port 1886
listener 1886 INADDR_ANY
  ipv6 true
```

4. Start the broker:

```
./broker_mqtts config.conf
```

You can refer to
https://rawgit.com/MichalFoksa/rsmb/master/rsmb/doc/gettingstarted.htm for more
configuration options.

---
