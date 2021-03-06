---
title: Custom Controllers
layout: page
---

All controllers have the attribute `mapping`, which is a key-value map. The key defines the event fired from the controller (you can check these events in the individual pages from the [supported controllers](/controllerx/controllers)). The value is defined depending on each custom controller.

## Custom light controller

Class: `LightController` or any LightController specific from a device (e.g. `E1743Controller`)

This controller lets you map controller events with predefined light actions. This is a [Light controller](/controllerx/start/type-configuration#light-controller), so it inheritance all its parameters. This is the list of predefined actions that can be mapped as a value in the key-value map from the `mapping` attribute.

| value                     | description                                                                                                                  |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `on`                      | It turns on the light                                                                                                        |
| `off`                     | It turns off the light                                                                                                       |
| `toggle`                  | It toggles the light                                                                                                         |
| `toggle_full_brightness`  | It toggles the light, setting the brightness to the maximum value when turning on.                                           |
| `toggle_full_white_value` | It toggles the light, setting the white value to the maximum value when turning on.                                          |
| `toggle_full_color_temp`  | It toggles the light, setting the color temperature to the maximum value when turning on.                                    |
| `toggle_min_brightness`   | It toggles the light, setting the brightness to the minimum value when turning on.                                           |
| `toggle_min_white_value`  | It toggles the light, setting the white value to the minimum value when turning on.                                          |
| `toggle_min_color_temp`   | It toggles the light, setting the color temperature to the minimum value when turning on.                                    |
| `release`                 | It stops `hold` actions                                                                                                      |
| `on_full_brightness`      | It puts the brightness to the maximum value                                                                                  |
| `on_full_white_value`     | It puts the white value to the maximum value                                                                                 |
| `on_full_color_temp`      | It puts the color temp to the maximum value                                                                                  |
| `on_min_brightness`       | It puts the brightness to the minimum value                                                                                  |
| `on_min_white_value`      | It puts the white value to the minimum value                                                                                 |
| `on_min_color_temp`       | It puts the color temp to the minimum value                                                                                  |
| `set_half_brightness`     | It sets the brightness to 50%                                                                                                |
| `set_half_white_value`    | It sets the white value to 50%                                                                                               |
| `set_half_color_temp`     | It sets the color temp to 50%                                                                                                |
| `sync`                    | It syncs the light(s) to full brightness and white colour or 2700K (370 mireds)                                              |
| `click_brightness_up`     | It brights up accordingly with the `manual_steps` attribute                                                                  |
| `click_brightness_down`   | It brights down accordingly with the `manual_steps` attribute                                                                |
| `click_white_value_up`    | It turns the white value up accordingly with the `manual_steps` attribute                                                    |
| `click_white_value_down`  | It turns the white value down accordingly with the `manual_steps` attribute                                                  |
| `click_color_up`          | It turns the color up accordingly with the `manual_steps` attribute                                                          |
| `click_color_down`        | It turns the color down accordingly with the `manual_steps` attribute                                                        |
| `click_colortemp_up`      | It turns the color temp up accordingly with the `manual_steps` attribute                                                     |
| `click_colortemp_down`    | It turns the color temp down accordingly with the `manual_steps` attribute                                                   |
| `click_xycolor_up`        | It turns the xy color up accordingly with the `manual_steps` attribute                                                       |
| `click_xycolor_down`      | It turns the xy color down accordingly with the `manual_steps` attribute                                                     |
| `hold_brightness_up`      | It brights up until release accordingly with the `automatic_steps` attribute                                                 |
| `hold_brightness_down`    | It brights down until release accordingly with the `automatic_steps` attribute                                               |
| `hold_brightness_toggle`  | It brights up/down until release accordingly with the `automatic_steps` attribute and alternates in each click               |
| `hold_white_value_up`     | It turns the white value up until release accordingly with the `automatic_steps` attribute                                   |
| `hold_white_value_down`   | It turns the white value down until release accordingly with the `automatic_steps` attribute                                 |
| `hold_white_value_toggle` | It turns the white value up/down until release accordingly with the `automatic_steps` attribute and alternates in each click |
| `hold_color_up`           | It turns the color up until release accordingly with the `automatic_steps` attribute                                         |
| `hold_color_down`         | It turns the color down until release accordingly with the `automatic_steps` attribute                                       |
| `hold_color_toggle`       | It turns the color up/down until release accordingly with the `automatic_steps` attribute and alternates in each click       |
| `hold_colortemp_up`       | It turns the color temp up until release accordingly with the `automatic_steps` attribute                                    |
| `hold_colortemp_down`     | It turns the color temp down until release accordingly with the `automatic_steps` attribute                                  |
| `hold_colortemp_toggle`   | It turns the color temp up/down until release accordingly with the `automatic_steps` attribute and alternates in each click  |
| `hold_xycolor_up`         | It turns the xy color up until release accordingly with the `automatic_steps` attribute                                      |
| `hold_xycolor_down`       | It turns the xy color down until release accordingly with the `automatic_steps` attribute                                    |
| `hold_xycolor_toggle`     | It turns the xy color up/down until release accordingly with the `automatic_steps` attribute and alternates in each click    |

#### Example of custom LightController

This is an example that uses the controller E1810 to put the brightness and color temperature to maximum when pressing the top or right button and to minumum when pressing the bottom or left ones. The key values where extracted from zigbee2mqtt section found in [here](/controllerx/controllers/E1524_E1810) and the values are from the list beforementioned.

```yaml
example_app:
  module: controllerx
  class: LightController
  controller: sensor.livingroom_controller_action
  integration: z2m
  light: light.livingroom
  mapping:
    toggle: toggle
    brightness_up_click: on_full_brightness
    brightness_down_click: on_min_brightness
    brightness_up_hold: on_full_brightness
    brightness_down_hold: on_min_brightness
    arrow_right_click: on_full_color_temp
    arrow_left_click: on_min_color_temp
    arrow_right_hold: on_full_color_temp
    arrow_left_hold: on_min_color_temp
```

## Custom media player controller

Class: `MediaPlayerController` or any MediaPlayerController specific from a device (e.g. `E1743MediaPlayerController`)

This controller lets you map controller events with predefined media player actions. This is a [Media player controller](/controllerx/start/type-configuration#media-player-controller), so it inheritance all its parameters. This is the list of predefined actions that can be mapped as a value in the key-value map from the `mapping` attribute.

| value             | description                                        |
| ----------------- | -------------------------------------------------- |
| hold_volume_down  | It turns the volume down until `release` is called |
| hold_volume_up    | It turns the volume up until `release` is called   |
| click_volume_down | It turns the volume down one step                  |
| click_volume_up   | It turns the volume up one step                    |
| release           | It calls `release` for `hold` actions              |
| play_pause        | It toggles the play/pause media                    |
| next_track        | It skips the track forward                         |
| previous_track    | It skips the track backward                        |
| next_source       | It changes to the next source                      |
| previous_source   | It changes to the previous source                  |

#### Example of custom MediaPlayerController

This is an example that uses the controller E1743 to control a media player using custom controller with deCONZ. The mapping from the deCONZ event ids can be found in [here](/controllerx/controllers/E1743) and the values are from the list beforementioned.

```yaml
example_app:
  module: controllerx
  class: E1743MediaPlayerController
  controller: livingroom-controller
  integration: deconz
  media_player: media_player.livingroom_speaker
  mapping:
    1002: play_pause
    2002: play_pause
    1001: hold_volume_up
    2001: hold_volume_down
    1003: release
    2003: release
```

## Custom switch controller

Class: `SwitchController` or any MediaPlayerController specific from a device (e.g. `E1743SwitchController`)

This controller lets you map controller events with predefined switch actions. This is a [Switch controller](/controllerx/start/type-configuration#switch-controller), so it inheritance all its parameters. This is the list of predefined actions that can be mapped as a value in the key-value map from the `mapping` attribute.

| value  | description                        |
| ------ | ---------------------------------- |
| on     | It turns the switch on             |
| off    | It turns the switch off            |
| toggle | It toggles the state of the switch |

#### Example of custom SwitchController

This is an example that uses the controller E1743 to toggle a switch with both, on and off states for ZHA. The mapping from the ZHA event ids can be found in [here](/controllerx/controllers/E1743) and the values are from the list under `ZHA`.

```yaml
example_app:
  module: controllerx
  class: SwitchController
  controller: 00:67:88:56:06:78:9b:3f
  integration: zha
  switch: switch.kitchen_dishwasher
  mapping:
    "on": toggle
    "off": toggle
```

## Custom cover controller

Class: `CoverController` or any MediaPlayerController specific from a device (e.g. `E1743CoverController`)

This controller lets you map controller events with predefined cover actions. This is a [Cover controller](/controllerx/start/type-configuration#cover-controller), so it inheritance all its parameters. This is the list of predefined actions that can be mapped as a value in the key-value map from the `mapping` attribute.

| value        | description                                        |
| ------------ | -------------------------------------------------- |
| open         | It opens the cover                                 |
| close        | It closes the cover                                |
| stop         | It stops the cover                                 |
| toggle_open  | It stops the cover if running and opens otherwise  |
| toggle_close | It stops the cover if running and closes otherwise |

#### Example of custom CoverController

This is an example that uses the controller E1810 to control a cover with Zigbee2MQTT. The mapping from the z2m event ids can be found in [here](/controllerx/controllers/E1524_E1810) and the values are from the list under `Zigbee2MQTT`.

```yaml
example_app:
  module: controllerx
  class: CoverController
  controller: sensor.e1810_controller
  integration: z2m
  cover: cover.kitchen
  mapping:
    brightness_up_click: toggle_open
    brightness_down_click: toggle_close
    brightness_up_hold: open
    brightness_up_release: stop
    brightness_down_hold: close
    brightness_down_release: stop
```

## Call service controller

Class: `Controller` or any type of Controller

This custom controller is the different one from the previous ones. This one allows you to freely call Home Assistant services when events are triggered. We can use `mapping` attribute like others and the use of the key value is the same, it defines the trigger event. However, the value changes since there are not predefined actions, you will need to specify the service (or services) and its data. We will see it better with an example.

Imagine I have a Hue dimmer switch and a normal light that only have on/off states (no brightness, no colors). Then I will be having two buttons that will be doing nothing. However, this controller will be used by my grandfather and he sometimes needs helps. Here is custom controller comes, so we can call two HA script (that do something useful for my grandfather) with the brightness up button and send a notification to Telegram with brightness down one.

```yaml
# We first define a HueDimmerController to control the light
# and just giving permission to the "on" and "off" buttons
hue_dimmer_example:
  module: controllerx
  class: HueDimmerController
  controller: sensor.office_controller_action
  integration: z2m
  light: light.office
  actions:
    - on-press
    - off-press

custom_hue_dimmer_example:
  module: controllerx
  class: HueDimmerController
  controller: sensor.office_controller_action
  integration: z2m
  mapping:
    up-press:
      - service: script.my_script
      - service: script.my_script2
        data:
          attr1: value
    down-press:
      service: notify.telegram
      data:
        message: Hey! Your abuelo is calling you, come and help him out.
```
