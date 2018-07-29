---
layout: page
title: "HomematicIP Cloud"
description: "Instructions for integrating HomematicIP into Home Assistant."
date: 2018-04-02 13:40
sidebar: true
comments: false
sharing: true
footer: true
ha_category: Hub
ha_iot_class: "Cloud Push"
ha_release: 0.66
featured: false
---

The [HomematicIP](http://www.homematic-ip.com) component platform is used as an interface to the cloud server.
For for communication [homematicip-rest-api](https://github.com/coreGreenberet/homematicip-rest-api) is used. Since there is no official documentation about this API everything was done via reverse engineering. Use at your own risk.

* To set up the component via interface (**Configuration->Integrations**):
  
  Fill the form:
  
    - your **access point ID** (SGTIN)
    - Optional a **name** to identify your access point, this will be used to prefix your device names.
  
  The **authtoken** will be generated and stored internaly.

* To set up the component via `configuration.yaml`:
  
  Generate the authentication token:  
  
    ```yaml
    generate_auth_token.py
    ```
  
  Add the information to your `configuration.yaml` file:

    ```yaml
    homematicip_cloud:
      - accesspoint: IDENTIFIER
        authtoken: AUTHTOKEN
      - name: Location2
        accesspoint: IDENTIFIER2
        authtoken: AUTHTOKEN2   
    ```

    Configuration variables (global):
      
      - name: (*Optional*): Name to identify your access point, this will be used to prefix your device names.
      - accesspoint: (*Required*): This is the access point id (SGTIN)
      - authtoken: (*Required*): Authentification token generated with `generate_auth_token.py`.

* Actual implemented and tested

  - homematicip_cloud.alarm_control_panel
  - [x] Security zones
  - homematicip_cloud.binary_sensor  
  - [x] Window and door contact (HmIP-SWDO)
  - [x] Smoke sensor and alarm (HmIP-SWSD) 
  - [x] Motion detectors (HmIP-SMI)
  - [x] Motion detectors (HmIP-SMI55)
  - homematicip_cloud.climate
  - [x] Radiator Thermostat (HmIP-eTRV,-2)
  -  homematicip_cloud.light
  - [x] Switch actuator and meter for brand switches (HmIP-BSM)
  - [x] Dimming actuator for brand switches (HmIP-BDT)
  - homematicip_cloud.sensor
  - [x] Wall-mounted thermostat (HmIP-WTH)
  - [x] Temperature and Humidity Sensor (HmIP-STH)
  - [x] Temperature and Humidity Sensor (HmIP-STHD
  - homematicip_cloud.switch
  - [x] Pluggable Switch and Meter (*HmIP-PSM*)
