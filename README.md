# meta-Tasmota
By Ton

This driver can control Sonoff devices when using Tasmota firmware on them.

## General information
Currently this driver supports Sonoff switches and dimmers; the latter not  tested as I only own switches.
The driver communicates with the Sonoff devivces over MQTT, so make sure that you've setup the MQTT section of the Tasmota firmware of your Sonoff device properly.
Because of limitations within the new Meta (versus the old metadriver) releases, it can not use dynamic discovery but uses static definition of the Tasmota device.

## Installation

- First step is to make sure that you Sonoff device is connected to the MQTT-broker ON YOUR meta-system.
  To do so, open the Tasmota GUI of your Sonoff device and go to configuration, then configure MQTT.
  Fill in the IP-address of the MQTT-broker of your meta (normally the same as the IP-address of meta) as host, port 1883.
  Then fill in the field topic with the name you want your Sonoff device to have. For example Tasmota_TV.
  save configuration and you're done with configuring The Tasmota firmware of your Sonoff device. 
- Then add the driver Tasmota.json, either via metacore or by fetching it from the internet and storing it in the active directory of meta.
- IMPORTANT!!!
  YOU HAVE TO configure the name you entered for your device (specified as topic, in the example Tasmota_TV) in the driver. So open the driver with an editor (f.e. nano) and change the text 
  ## PLACE THE NAME OF YOUR DEVICE (AS KNOWN IN MQTT) HERE ## f.e.Tasmota_TV
  by the chosen name (the example Tasmota_TV). 
  Save it and restart meta.
- You can now use the NEEO GUI and search for the device "Tasmota" and add it, thena dding shortcuts. Please note:      "power on" and "power off" do not change the state, use "LIGHT ON" and "LIGHT OFF" to do so.

## Special instructions for multiple devices
As meta  urrently doesn;t offer enough facilities to support dynamic discovery, you have to add and configre a driver manually.
If you want to control multiple devices, you can add and configure multiple drivers to meta. 
To do so, every driver-name has to be unique (both the filename AND the name within the driver).
I suggest to use a meningful name for the driver's internal and file name, like Tasmota_TV, Tasmota_Bedroom etc.   
