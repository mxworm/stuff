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

* Configuration via interface:
  
  Fill the form:
    - your **access point ID** (SGTIN)
    - Optional a **name** to identify your access point, this will be used to prefix your device names.
  The **authtoken** will be generatetd internaly and stored


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

      - **name** (*Optional*): Name to identify your access point, this will be used to prefix your device names.
      - **accesspoint** (*Required*): This is the access point id (SGTIN)
      - **authtoken** (*Required*): Authentification token generated with `generate_auth_token.py`.

