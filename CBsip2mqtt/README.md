# CB sip2mqtt

Important! Install process may take up to 5 minutes, let it do its things.

Dockerfile inspired by 

MartyTremblay / https://github.com/MartyTremblay/pjsip-docker 
Raph2i https://github.com/raph2i/hassio-addons
minoruta / https://github.com/minoruta/pjsip-node-alpine

## configuration.yaml
```
sensor:
  - platform: mqtt
    name: sip2mqtt
    state_topic: "home/sip"
    value_template: '{{ value_json.verb }}'
    json_attributes_topic: "home/sip"
```

## hass sensor
![alt text](https://raw.githubusercontent.com/CB69/hassio-addons/master/CBsip2mqtt/pic.png "mqtt_sensor")
