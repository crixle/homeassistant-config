

# Crixle's Dashboard
I've always loved HomeKit, but it lacks functionality and integration with many of my devices so I created this dashboard to give off iOS vibes but gives me the versatility my smart home needs. </br>
</br>
**NOTE: Some cards have their code provided allowing simple copy and pasting into your own dash, however most require button templates provides in the rep files. As always, replace my entities with yours otherwise cards won't work.**


![Screenshot 2022-01-02 103557](https://user-images.githubusercontent.com/54859942/148412043-ec17e2d0-6dfa-4c91-8111-65b64a6ffe62.png)




### Features
- Adaptive layout thanks to [Layout Card](https://github.com/thomasloven/lovelace-layout-card)
- [Light control center that switches between rooms](#light-control-card)
- [Dynamic Floor Plan](#floor-plan)
- Arlo Pro 3 camera control/library access
- [Automatic light/dark mode](#useful-automations)

Home Assistant Hardware| Quantity | Find
-------- | -------- | ------
Raspberry Pi 4B 4GB | 1 | link
Samsung 500GB SSD via USB | 1 | [link](https://www.bestbuy.com/site/samsung-t7-500gb-external-usb-3-2-gen-2-portable-solid-state-drive-with-hardware-encryption-indigo-blue/6408298.p?skuId=6408298)
HUSBZB USB Hub (Zigbee & Z-Wave) |1 | [link](https://www.amazon.com/gp/product/B01GJ826F8/ref=ppx_yo_dt_b_asin_title_o03_s00?ie=UTF8&psc=1)
Philips Hue A19 Bulbs + Hub (1) | 26ish | [link](https://www.bestbuy.com/site/philips-hue-white-and-color-ambiance-a19-bluetooth-75w-smart-led-starter-kit/6472224.p?skuId=6472224)
Budget Friendly Zigbee Bulbs (Temp Only) | 6 | [link](https://www.homedepot.com/p/EcoSmart-60-Watt-Equivalent-A19-Dimmable-SMART-LED-Light-Bulb-Tunable-White-2-Pack-A9A19A60WESDZ02/309683612)
Amazon HD Fire 10 (2019) w/ [WallPanel](https://play.google.com/store/apps/details?id=com.thanksmister.iot.wallpanel&hl=en_US&gl=US) | 1 |

Devices | Quantity | Find
-------- | -------- | ------ 
Aqara Sensors (Motion, Temp/Hum) | 3 | [link](https://www.aqara.com/us/home.html)
Philips Motion Sensor | 3 | [link](https://www.bestbuy.com/site/philips-hue-motion-sensor-white/5540102.p?skuId=5540102)
Philips Sync Box | 1 | [link](https://www.bestbuy.com/site/philips-hue-play-hdmi-sync-box-black/6371722.p?skuId=6371722)
Philips 55" Gradient Strip | 1 | [link](https://www.bestbuy.com/site/philips-hue-play-gradient-lightstrip-55/6427737.p?skuId=6427737)
JHome Zigbee Smart Plugs | 4 | [link](https://www.amazon.com/gp/product/B08K7FY2GP/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)


  
  # HACS Addons
  | Card | Link | Card | Link
  | :--- | ---- | ---- | ----
  | Button Card | [link](https://github.com/custom-cards/button-card) | Vertical Stack In Card | [link](https://github.com/custom-cards/vertical-stack-in-card) | CSS Card Mod | [link](https://github.com/thomasloven/lovelace-card-mod) |
  | Layout Card | [link](https://github.com/thomasloven/lovelace-layout-card) | Light Popup Card | [link](https://github.com/DBuit/light-popup-card) |
  | Auto Entities | [link](https://github.com/thomasloven/lovelace-auto-entities) | Browser Mod | [link](https://github.com/thomasloven/hass-browser_mod) |
  | State-Switch | [link](https://github.com/thomasloven/lovelace-state-switch) | Home Feed Card | [link](https://github.com/gadgetchnnel/lovelace-home-feed-card) |
  | Mini Media Player | [link](https://github.com/kalkih/mini-media-player) | Aarlo | [link](https://github.com/twrecked/lovelace-hass-aarlo) |
  | Swipe Card | [link](https://github.com/bramkragten/swipe-card) | Theme | [link](https://github.com/basnijholt/lovelace-ios-themes) |
  | Paper Buttons | [link](https://github.com/jcwillox/lovelace-paper-buttons-row) | Layout Card | [link](https://github.com/thomasloven/lovelace-layout-card) |
  | Kiosk Mode | [link](https://github.com/maykar/kiosk-mode) | Hue Icons | [link](https://github.com/arallsopp/hass-hue-icons)
  | Uptime Card | [link](https://github.com/dylandoamaral/uptime-card) | Simple Thermostat | [link](https://github.com/nervetattoo/simple-thermostat)
  



# Room Tabs
  
  I've retired my old method of room control, which was a [state-switch card](https://github.com/thomasloven/lovelace-state-switch) with all the lights organized by room. Due to it's instability and performance issues, I've created room tabs! Room tabs show me what I need to know about the rooms at a glance but let me change the lights and the TV when I click on it.
 
![RoomTabs](https://user-images.githubusercontent.com/54859942/148406102-01ded048-724e-467f-9da5-106450363cfc.gif)
Each room card is based off a [group](https://www.home-assistant.io/integrations/group/) that automatically populates on boot or when I tell it to. See [auto-populating groups](#auto-populating-groups) for more info!

![RoomTabPopup](https://user-images.githubusercontent.com/54859942/148413959-ef7da284-0e72-4492-aa83-308575e6d032.gif)


##### ! For fans and media players, they are using a button-card template which can be found up in the files. 

<details>
  <summary>Card Code (use in vertical-stack)</summary>
  
```
type: custom:button-card
show_label: true
label: |
  [[[
    return states['sensor.boudoir_lights_on'].state + " lights on"
  ]]]
name: |
  [[[
    return states['group.boudoir_lights'].attributes.friendly_name + " " +
    `<span style="background: rgba(255,255,255,.1); padding: 1px 5px; border-radius: 20px;">
    ${Math.round(states['sensor.boudoir_temperature'].state)}°F
    </span>`
  ]]]
entity: group.boudoir_lights
tap_action:
  haptic: medium
  action: more-info
hold_action:
  action: more-info
show_state: false
state:
  - value: 'off'
    styles:
      icon:
        - filter: grayscale(100%) opacity(50%)
      name:
        - filter: grayscale(100%) opacity(50%)
      label:
        - filter: grayscale(100%) opacity(50%)
styles:
  card:
    - padding: 5px
  icon:
    - width: 60px
    - transition: filter 1s
    - filter: drop-shadow( 3px 3px 2px rgba(0, 0, 0, .3))
  img_cell:
    - width: 60px !important
  label:
    - place-self: start
    - font-size: 20px
    - overflow: visible
  name:
    - place-self: end
    - justify-self: start
    - font-size: 20px
    - overflow: visible
  grid:
    - grid-template-columns: 17% 80px repeat(4, 1fr)
    - grid-template-rows: 1fr 1fr
    - grid-template-areas: |
        "i n n wid1 wid2 lights"
        "i l l wid1 wid2 lights"
  custom_fields:
    temp:
      - place-self: center
      - font-size: 18px
      - background: rgba(255,255,255,.1)
      - padding: 1px 3px
      - border-radius: 15px
      - mix-blend-mode: difference
custom_fields:
  wid1:
    card:
      type: custom:button-card
      entity: switch.air_purifier
      template: room_card_fan
  wid2:
    card:
      type: custom:button-card
      entity: media_player.boudoir_system
      template: room_card_media
  lights:
    card:
      type: custom:button-card
      show_state: true
      entity: group.boudoir_lights
      icon: mdi:lamps
      state:
        - value: 'off'
          styles:
            icon:
              - filter: grayscale(100%) opacity(50%)
            state:
              - filter: grayscale(100%) opacity(50%)
      show_name: false
      styles:
        card:
          - background: none
          - box-shadow: none
          - border-radius: 0
        icon:
          - width: 40px
          - transition: filter 1s



  ```
</details>
<details>
  <summary>Lights On Sensors (configuration.yaml)</summary>
  
```
sensor:                                                
  - platform: template
    sensors:
      kitchen_lights_on:
        value_template: "{{ states.light | selectattr('state', 'eq', 'on') | map(attribute='entity_id') | map('area_name')| select('in', ['Kitchen'])| list | count}}"
      livingroom_lights_on:
        value_template: "{{ states.light | selectattr('state', 'eq', 'on') | map(attribute='entity_id') | map('area_name')| select('in', ['Living Room'])| list | count}}"
      office_lights_on:
        value_template: "{{ states.light | selectattr('state', 'eq', 'on') | map(attribute='entity_id') | map('area_name')| select('in', ['Office'])| list | count}}"
      bedroom_lights_on:
        value_template: "{{ states.light | selectattr('state', 'eq', 'on') | map(attribute='entity_id') | map('area_name')| select('in', ['Bedroom'])| list | count}}"
      boudoir_lights_on:



  ```
</details>



                     
# Floor Plan
  
  This card is my favorite because it's informative and let's me look at the entire house in a glance. Best part is that it was relatively easy to make with a bit of patience. I followed [this guide](https://community.home-assistant.io/t/floorplan-ui-with-color-synced-lights/169417) and had it working within a couple hours. The guide allows you to sync the color to match color and brightness, but I had issues with color matching not being accurate so I just match brightness.
  ![floorplan](https://user-images.githubusercontent.com/54859942/120511145-1e8e0000-c398-11eb-93af-11c22549a6e9.gif)
##### This code is very complex, and will not work on your dash by copying and pasting. Because it's using JavaScript to work, if any of the entities are incorrect it will just crash and not load anything. Use my code as a reference to yours.
<details>
  <summary>Code</summary>
  
   ```
    type: 'custom:stack-in-card'
    style: |
      ha-card {
        background: var( --ha-card-background, var(--card-background-color, white) );
        padding: 10px;
        border-radius: 30px;
        box-shadow: 0 5px 18px rgba(0,0,0,.2);
        }
    cards:
      - type: 'custom:config-template-card'
        entities:
          - light.desk_lamp
          - light.standing_lamp
          - light.boudoir_ceiling_light
          - light.nanoleaf
          - light.bedside_lamp
          - light.bedroom_floor_lamp
          - light.vine_lights
          - light.closet_1
          - light.hue_play_gradient_lightstrip_1
          - light.office_strip
          - light.office_lamp_1
          - light.desk_lamp_2
        card:
          type: picture-elements
          image: /local/floorplan/base/floorday.png
          elements:
            - type: conditional
              conditions:
                - entity: light.desk_lamp
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/boudoirdesklamp.png
                  style:
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.standing_lamp
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/boudoirstanding_lamp.png
                  style:
                    opacity: '${ states[''light.standing_lamp''].attributes.brightness / 255 }'
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.boudoir_ceiling_light
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/boudoirceilinglight.png
                  style:
                    opacity: >-
                      ${ states['light.boudoir_ceiling_light'].attributes.brightness
                      / 255 }
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.nanoleaf
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/boudoirnanoleaf.png
                  style:
                    opacity: '${ states[''light.nanoleaf''].attributes.brightness / 255 }'
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.bedside_lamp
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/bedroombedsidelamp.png
                  style:
                    opacity: '${ states[''light.bedside_lamp''].attributes.brightness / 255 }'
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.bedroom_floor_lamp
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/bedroomfloorlamp.png
                  style:
                    opacity: >-
                      ${ states['light.bedroom_floor_lamp'].attributes.brightness /
                      255 }
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.vine_lights
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/bedroomvinelights.png
                  style:
                    opacity: '${ states[''light.vine_lights''].attributes.brightness / 255 }'
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.closet_1
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/boudoircloset.png
                  style:
                    opacity: '${ states[''light.closet_1''].attributes.brightness / 255 }'
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.hue_play_gradient_lightstrip_1
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/boudoirtv.png
                  style:
                    opacity: >-
                      ${
                      states['light.hue_play_gradient_lightstrip_1'].attributes.brightness
                      / 255 }
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: switch.clem
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/officeclem.png
                  style:
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.office_strip
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/officestrip.png
                  style:
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
                    opacity: '${ states[''light.office_strip''].attributes.brightness / 255 }'
            - type: conditional
              conditions:
                - entity: light.office_lamp_1
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/officedesklamp1.png
                  style:
                    filter: >-
                      ${ "hue-rotate(" +
                      (states['light.office_lamp_1'].attributes.hs_color ?
                      states['light.office_lamp_1'].attributes.hs_color[0] : 0) +
                      "deg)"}
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
                    opacity: '${ states[''light.office_lamp_1''].attributes.brightness / 255 }'
            - type: conditional
              conditions:
                - entity: light.desk_lamp_2
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/officedesklamp2.png
                  style:
                    filter: >-
                      ${ "hue-rotate(" +
                      (states['light.desk_lamp_2'].attributes.hs_color ?
                      states['light.desk_lamp_2'].attributes.hs_color[0] : 0) +
                      "deg)"}
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
                    opacity: '${ states[''light.desk_lamp_2''].attributes.brightness / 255 }'
            - type: 'custom:button-card'
              style:
                height: 7%
                width: 7%
                left: 73.5%
                top: 5%
              entity: light.nanoleaf
              template: floorbutton
            - type: 'custom:button-card'
              style:
                height: 7%
                width: 7%
                left: 90%
                top: 7%
              entity: light.desk_lamp
              template: floorbutton
            - type: 'custom:button-card'
              style:
                height: 7%
                width: 7%
                left: 95%
                top: 85%
              entity: light.standing_lamp
              template: floorbutton
            - type: 'custom:button-card'
              style:
                height: 7%
                width: 7%
                left: 80%
                top: 55%
              entity: light.boudoir_ceiling_light
              template: floorbutton
            - type: 'custom:button-card'
              style:
                height: 7%
                width: 7%
                left: 38%
                bottom: 7%
              entity: light.vine_lights
              template: floorbutton
            - type: 'custom:button-card'
              style:
                height: 7%
                width: 7%
                left: 35%
                bottom: 15%
              entity: light.bedroom_floor_lamp
              template: floorbutton
            - type: 'custom:button-card'
              style:
                height: 7%
                width: 7%
                left: 57%
                top: 7%
              entity: light.bedside_lamp
              template: floorbutton
            - type: state-icon
              entity: media_player.boudoir_tv_2
              style:
                top: 25%
                right: 27.5%
            - type: state-icon
              entity: switch.air_purifier
              icon: 'hass:air-purifier'
              tap_action:
                action: toggle
              style:
                right: 27%
                bottom: 25%
            - type: state-label
              entity: sensor.lumi_lumi_weather_0a037c06_temperature
              style:
                color: white
                left: 15%
                bottom: '-5%'
      - type: 'custom:config-template-card'
        entities:
          - light.hue_white_lamp_1
          - light.living_room_couch_lamp
          - light.kitchen_island_lighting
          - light.living_room_ceiling_light_1
          - light.hall_lamp
        card:
          type: picture-elements
          image: /local/floorplan/base/downstairsday.png
          elements:
            - type: conditional
              conditions:
                - entity: light.hue_white_lamp_1
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/kitchenceiling.png
                  style:
                    opacity: >-
                      ${ states['light.hue_white_lamp_1'].attributes.brightness /
                      255 }
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.living_room_couch_lamp
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/livingroomlamp.png
                  style:
                    opacity: >-
                      ${
                      states['light.living_room_couch_lamp'].attributes.brightness /
                      255 }
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.kitchen_island_lighting
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/kitchenislandlights.png
                  style:
                    opacity: >-
                      ${
                      states['light.kitchen_island_lighting'].attributes.brightness
                      / 255 }
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.living_room_ceiling_light_1
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/livingroomlights.png
                  style:
                    opacity: >-
                      ${
                      states['light.living_room_ceiling_light_1'].attributes.brightness
                      / 255 }
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: conditional
              conditions:
                - entity: light.hall_lamp
                  state: 'on'
              elements:
                - type: image
                  image: /local/floorplan/lights/livingroomwalllight.png
                  style:
                    opacity: '${ states[''light.hall_lamp''].attributes.brightness / 255 }'
                    width: 100%
                    height: 100%
                    top: 50%
                    left: 50%
                    mix-blend-mode: lighten
            - type: 'custom:button-card'
              style:
                height: 7%
                width: 7%
                left: 20%
                top: 48%
              entity: group.kitchen
              template: floorbutton
            - type: 'custom:button-card'
              style:
                height: 7%
                width: 7%
                left: 55%
                top: 48%
              entity: group.livingroom
              template: floorbutton
            - type: state-icon
              entity: vacuum.rug_b
              tap_action:
                action: toggle
              style:
                left: 10%
                bottom: 0%
            - type: state-label
              entity: lock.back_door
              tap_action:
                action: toggle
              style:
                right: '-7%'
                bottom: 8%
                color: white
            - type: state-label
              entity: lock.front_door
              tap_action:
                action: toggle
              style:
                left: 7%
                top: 30%
                color: white
            - type: state-label
              entity: lock.front_door
              tap_action:
                action: toggle
              style:
                left: 7%
                top: 30%
                color: white
            - type: conditional
              conditions:
                - entity: sensor.washer
                  state: 'on'
              elements:
                - type: state-label
                  entity: sensor.washer_remaining_time
                  style:
                    right: 5%
                    top: 17.5%
                    color: white
                - type: 'custom:text-element'
                  text: m
                  style:
                    right: 5%
                    top: 17.5%
                    color: white
            - type: conditional
              conditions:
                - entity: sensor.dryer
                  state: 'on'
              elements:
                - type: state-label
                  entity: sensor.dryer_remaining_time
                  style:
                    right: 5%
                    top: 31%
                    color: white
                - type: 'custom:text-element'
                  text: m
                  style:
                    right: 5%
                    top: 31%
                    color: white

  ```

</details>

# Auto-Populating Groups
So, picture this. You just replaced a Hue bulb in your bedroom and now you need to go update it in Home Assistant. You've done that and all is well again, until you go to bed.
In your excitement, you didn't add the new bulb to the correct room in Google Home. So when you say, "Hey Google, turn off the lights", it turns them all off except the new one.
Now, you have to get up and MANUALLY turn off that light like a CAVEMAN and dump your sorry ass back into bed. So to prevent that from happening again, I created this script.

When I add/replace lights in my home, it's incredibly annoying to have to go modify Home Assistant, HomeKit, and Google Assistant when I really only use HK and GA for turning lights on and off. So, my solution was to create groups that automatically create themselves based off areas with a simple script. All I have to do is setup the device in HA then add it to the appropriate area and the rest is automatic. Only the 'group' entities are exposed to GA and HK so that when I say "turn off the lights", it turns off the lights based off the Home Assistant area. 
The script is ran everytime Home Assistant starts or if I manually call it. 
<details>
  <summary>Code</summary>
  
```
alias: Sync Areas to Light Groups
description: Gets entities within all areas and creates auto-populating groups
trigger:
  - platform: homeassistant
    event: start
condition: []
action:
  - service: group.set
    data:
      object_id: boudoir_lights
      name: Boudoir
      icon: hue:room-lounge
      entities: |
        {{ 
          expand(states.light) 
          |selectattr('entity_id', 'in', area_entities('Boudoir'))
          |map(attribute='entity_id')
          |list
        }}
  - service: group.set
    data:
      object_id: bedroom_lights
      name: Bedroom
      icon: hue:room-bedroom
      entities: |
        {{ 
          expand(states.light) 
          |selectattr('entity_id', 'in', area_entities('Bedroom'))
          |map(attribute='entity_id')
          |list
        }}
  - service: group.set
    data:
      object_id: office_lights
      name: Office
      icon: hue:room-office
      entities: |
        {{ 
          expand(states.light) 
          |selectattr('entity_id', 'in', area_entities('Office'))
          |map(attribute='entity_id')
          |list
        }}
  - service: group.set
    data:
      object_id: living_room_lights
      name: Living Room
      icon: mdi:sofa
      entities: |
        {{ 
          expand(states.light) 
          |selectattr('entity_id', 'in', area_entities('Living Room'))
          |map(attribute='entity_id')
          |list
        }}
  - service: browser_mod.toast
    data:
      message: Successfully refreshed light groups!
mode: single




  ```
</details>

# Theme
  
  My light theme is heavily built upon [ios dark mode themes](https://github.com/basnijholt/lovelace-ios-dark-mode-theme) with some tweaks and a custom background made by me! I recently got a new laptop with an OLED screen so I've fully embraced the dark side with my dark theme. Both the background and the code is provided in the files!
 ##### Optional: The font I'm using is [Outfit](https://fonts.google.com/specimen/Outfit) and you have to import that into your dashboard resources! Check out [this guide](https://community.home-assistant.io/t/adding-resources-to-lovelace/180729) and look at the 2nd post for reference!
 

# Wall Mounted Tablet
  
  I have a Kindle Fire 10 (2019) mounted to the wall with a few command strips, and it works beautifully! I initially used FullyKiosk to isolate Home Assistant, however it can only access a really old version of Android WebView which made it really slow and unresponsive. I was shocked when I tried WallPanel and it works almost flawlessly! I know leaving the Kindle plugged in 24/7 is really bad for the battery but :shrug:
 ![IMG_2713](https://user-images.githubusercontent.com/54859942/132931199-e96f00c3-869d-463b-91e6-b6e130540f9a.JPG)

# Motion Lights Automation

  ### Make sure you understand the code and modify as necessary!
  
  <details>
  	<summary>Motion Lights with time based brightnesses</summary>
  
  ```
alias: Hall Motion Lights
description: ''
trigger:
  - type: occupied
    platform: device
    device_id: 182bb3b5150abbefa4916f863008bb75
    entity_id: binary_sensor.bathroom_hall_motion_sensor_occupancy
    domain: binary_sensor
condition:
  - condition: or
    conditions:
      - condition: state
        entity_id: person.xxx
        state: home
      - condition: state
        entity_id: person.xxx
        state: home
action:
  - choose:
      - conditions:
          - condition: time
            after: '22:00'
            before: '08:00:00'
        sequence:
          - service: light.turn_on
            target:
              device_id:
                - 345a2abaf6f0eef2d51f92cf51affa9b
                - 6949950b1a739fd3207efdc18b72307c
            data:
              brightness_pct: 20
          - wait_for_trigger:
              - type: not_occupied
                platform: device
                device_id: 182bb3b5150abbefa4916f863008bb75
                entity_id: binary_sensor.bathroom_hall_motion_sensor_occupancy
                domain: binary_sensor
                for:
                  hours: 0
                  minutes: 0
                  seconds: 0
                  milliseconds: 0
          - service: light.turn_off
            target:
              device_id:
                - 6949950b1a739fd3207efdc18b72307c
                - 345a2abaf6f0eef2d51f92cf51affa9b
    default:
      - service: light.turn_on
        target:
          device_id:
            - 345a2abaf6f0eef2d51f92cf51affa9b
            - 6949950b1a739fd3207efdc18b72307c
        data:
          brightness_pct: 80
      - wait_for_trigger:
          - type: not_occupied
            platform: device
            device_id: 182bb3b5150abbefa4916f863008bb75
            entity_id: binary_sensor.bathroom_hall_motion_sensor_occupancy
            domain: binary_sensor
            for:
              hours: 0
              minutes: 3
              seconds: 0
              milliseconds: 0
      - service: light.turn_off
        target:
          device_id:
            - 345a2abaf6f0eef2d51f92cf51affa9b
            - 6949950b1a739fd3207efdc18b72307c
mode: single

  ```

</details>
