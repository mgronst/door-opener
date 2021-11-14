# door-opener project
The code is written to a ESP32/NodeMCU to be able to remotely open a frontdoor from
a calling system. 

The device needs to connect to a MQTT broker via Wifi and listens for a specific payload:
```{"status" : "on"}``` on the topic ```home/frontdoor```

You will also need an relay to connect to one of the ouput pins of the ESP32, and wire the output of
the relay to the wires that controll the push button on the calling system that opens the door.

Under the ```include``` folder you also need a file with the secrets. Call this ```secrets.h```, and input your
MQTT and Wifi secrets here. Example:
```
const char* WIFI_SSID = "ssid";
const char* WIFI_PASSWD = "pass";

const char* MQTT_HOST = "host";
const char* MQTT_USER = "user";
const char* MQTT_PASSWD = "pass";
```

## Hardware
The following ESP32 should work:
https://artigereliv.no/produkt/elektronikk/mikrokontrollere/nodemcu/esp32-nodemcu
The followin relay module should work:
https://www.kjell.com/no/produkter/elektro-og-verktoy/arduino/moduler/relemodul-for-arduino-1x-p87032

## Integration
* Home Assistant - MQTT is supported directly, and a MQTT button can be used in the user interface. 
* Google Assistant - Can be integrated with e.g. IFTT to send a webhook to some system that can trigger an MQTT publish based on the webhook.
* iOS Siri - The Shortcuts functionality can be used to send a webhook to some system that can trigger an MQTT publish.
