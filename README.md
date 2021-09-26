# Crixle's Dashboard
I've always loved HomeKit, but it lacks functionality and integration with many of my devices so I created this dashboard to give off iOS vibes but gives me the versatility my smart home needs. </br>
</br>
**NOTE: All cards have their code provided allowing simple copy and pasting into your own dash, however most require button templates provides in the rep files. As always, replace my entities with yours otherwise cards won't work.**


![LightDash](https://user-images.githubusercontent.com/54859942/134824129-26653897-72fc-493c-a200-f5dcb984680a.png)




### Features
- Adaptive layout thanks to [Layout Card](https://github.com/thomasloven/lovelace-layout-card)
- [Light control center that switches between rooms](#light-control-card)
- [Dynamic Floor Plan](#floor-plan)
- Arlo Pro 3 camera control/library access
- [Automatic light/dark mode](#useful-automations)
- [Media & Sync Box Control](#media-card)
- Room tracking for automations using [RoomAssistant](https://www.room-assistant.io/)

Hardware | Quantity | Find
-------- | -------- | ------
Raspberry Pi 4B 4GB | 1 | link
Samsung 500GB SSD via USB | 1 | [link](https://www.bestbuy.com/site/samsung-t7-500gb-external-usb-3-2-gen-2-portable-solid-state-drive-with-hardware-encryption-indigo-blue/6408298.p?skuId=6408298)
HUSBZB USB Hub (Zigbee & Z-Wave) |1 | [link](https://www.amazon.com/gp/product/B01GJ826F8/ref=ppx_yo_dt_b_asin_title_o03_s00?ie=UTF8&psc=1)
Philips Hue A19 Bulbs + Hub (1) | 26 | [link](https://www.bestbuy.com/site/philips-hue-white-and-color-ambiance-a19-bluetooth-75w-smart-led-starter-kit/6472224.p?skuId=6472224)
Budget Friendly Zigbee Bulbs (Temp Only) | 6 | [link](https://www.homedepot.com/p/EcoSmart-60-Watt-Equivalent-A19-Dimmable-SMART-LED-Light-Bulb-Tunable-White-2-Pack-A9A19A60WESDZ02/309683612)
Amazon HD Fire 10 (2019) w/ [WallPanel](https://play.google.com/store/apps/details?id=com.thanksmister.iot.wallpanel&hl=en_US&gl=US) | 1 | 
Aqara Sensors (Motion, Temp/Hum) | 3 | [link](https://www.aqara.com/us/home.html)
Philips Motion Sensor with ambient temperature | 3 | [link](https://www.bestbuy.com/site/philips-hue-motion-sensor-white/5540102.p?skuId=5540102)
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
 


<details>
  <summary>Dark Mode </summary>
  
  ![DarkDash](https://user-images.githubusercontent.com/54859942/132930231-127aca01-695a-44e3-8608-d935f75408b8.png)

</details>
<details>
  <summary>Wall Mounted Tablet</summary>
  
  I have a Kindle Fire 10 (2019) mounted to the wall with a few command strips, and it works beautifully! I initially used FullyKiosk to isolate Home Assistant, however it can only access a really old version of Android WebView which made it really slow and unresponsive. I was shocked when I tried WallPanel and it works almost flawlessly! I know leaving the Kindle plugged in 24/7 is really bad for the battery but :shrug:
 ![IMG_2713](https://user-images.githubusercontent.com/54859942/132931199-e96f00c3-869d-463b-91e6-b6e130540f9a.JPG)


</details>

# Theme
  
  You probably recognized my light mode theme, probably because it's one of the [ios dark mode themes](https://github.com/basnijholt/lovelace-ios-dark-mode-theme) with some tweaks and a custom background made by me! Both the background and the code is provided in the files!
 ##### Optional: The font I'm using is [DM Sans](https://fonts.google.com/specimen/DM+Sans) and you have to import that into your dashboard resources! Check out [this guide](https://community.home-assistant.io/t/adding-resources-to-lovelace/180729) and look at the 2nd post for reference!



# Light Control Card
  
  Control multiple lights and devices per room all while in one card! If the globe for a room is glowing, then that means lights are on in that room. Holding down on the globe will toggle them. Achieved by grouping the lights by rooms into grids, then using a state-switch card based off of the URL hash. Open the link above for more info.
 
  ![Lights](https://user-images.githubusercontent.com/54859942/132930244-e507add3-2313-4adf-bafd-ea6ed2581dff.gif)

<details>
  <summary>Code</summary>
  
```
type: vertical-stack
cards:
  - type: entities
    style: |
      ha-card {
        background: none;
        box-shadow: none;
        }
    entities:
      - type: custom:paper-buttons-row
        buttons:
          - entity: group.boudoir
            name: false
            icon: hass:sofa-single
            style:
              button:
                background: rgba(255,255,255,.1)
                box-shadow: >
                  {% if is_state('group.boudoir', 'on') %}

                  0px 8px 15px rgba(0, 0, 0, 0.2), inset 0 0 10px
                  rgba(255,255,255,.5)

                  {% else %}
                    0px 8px 15px rgba(0, 0, 0, 0.2);
                  {% endif %}
                border-radius: 50px
                padding: 20px
                color: |
                  {% if is_state('group.boudoir', 'on') %}
                    white
                  {% else %}
                    rgba(0,0,0,.5)
                  {% endif %}
              icon:
                '--mdc-icon-size': 40px
            state_styles:
              '#boudoir':
                button:
                  background: rgba(255,255,255,.5)
                  box-shadow: 0 0 15px rgba(255,255,255,.6)
            tap_action:
              action: navigate
              navigation_path: '#boudoir'
            hold_action:
              action: toggle
          - entity: group.bedroom
            name: false
            icon: hass:bed-king
            style:
              button:
                background: rgba(255,255,255,.1)
                border-radius: 50px
                padding: 20px
                box-shadow: |
                  {% if is_state('group.bedroom', 'on') %}
                   0px 8px 15px rgba(0, 0, 0, 0.2), inset 0 0 10px rgba(255,255,255,.5)
                  {% else %}
                    0px 8px 15px rgba(0, 0, 0, 0.2);
                  {% endif %}
                color: |
                  {% if is_state('group.bedroom', 'on') %}
                    white
                  {% else %}
                    rgba(0,0,0,.5)
                  {% endif %}
              icon:
                '--mdc-icon-size': 40px
            tap_action:
              action: navigate
              navigation_path: '#bedroom'
            hold_action:
              action: toggle
          - entity: group.office
            name: false
            icon: hass:laptop
            style:
              button:
                background: rgba(255,255,255,.1)
                border-radius: 50px
                padding: 20px
                box-shadow: |
                  {% if is_state('group.office', 'on') %}
                    0px 8px 15px rgba(0, 0, 0, 0.2),inset 0 0 10px rgba(255,255,255,.5)
                  {% else %}
                    0px 8px 15px rgba(0, 0, 0, 0.2);
                  {% endif %}
                color: |
                  {% if is_state('group.office', 'on') %}
                    white
                  {% else %}
                    rgba(0,0,0,.5)
                  {% endif %}
              icon:
                '--mdc-icon-size': 40px
            tap_action:
              action: navigate
              navigation_path: '#office'
            hold_action:
              action: toggle
          - entity: group.kitchen
            name: false
            icon: hass:stairs-down
            style:
              button:
                background: rgba(255,255,255,.1)
                border-radius: 50px
                padding: 20px
                box-shadow: |
                  {% if is_state('group.kitchen', 'on') %}
                   0px 8px 15px rgba(0, 0, 0, 0.2), inset 0 0 10px rgba(255,255,255,.5)
                  {% else %}
                    0px 8px 15px rgba(0, 0, 0, 0.2);
                  {% endif %}
                color: |
                  {% if is_state('group.kitchen', 'on') %}
                    white
                  {% else %}
                    rgba(0,0,0,.5)
                  {% endif %}
              icon:
                '--mdc-icon-size': 40px
            tap_action:
              action: navigate
              navigation_path: '#downstairs'
            hold_action:
              action: toggle
    view_layout:
      grid-area: orbs
      place-self: end stretch
  - type: entities
    entities:
      - type: custom:state-switch
        entity: hash
        default: boudoir
        states:
          boudoir:
            type: custom:mod-card
            card:
              type: custom:auto-entities
              card:
                type: grid
                square: false
                columns: 3
              filter:
                include:
                  - domain: light
                    area: Boudoir
                    options:
                      type: custom:button-card
                      template:
                        - grid_card
                        - light
                  - entity_id: light.boudoir_ceiling_light
                    options:
                      type: custom:button-card
                      template:
                        - grid_card
                        - light
                  - entity_id: light.tv_bars
                    options:
                      type: custom:button-card
                      template:
                        - grid_card
                        - light
                  - entity_id: media_player.boudoir_tv_2
                    options:
                      type: custom:button-card
                      tap_action:
                        action: more-info
                      template:
                        - grid_card
                        - tv
                  - entity_id: switch.air_purifier
                    options:
                      type: custom:button-card
                      template:
                        - grid_card
                      state:
                        - value: 'on'
                          spin: true
                exclude:
                  - entity_id: light.ceiling_1
                  - entity_id: light.ceiling_2
                  - entity_id: light.hue_play_1
                  - entity_id: light.hue_play_1_2
              card_param: cards
          bedroom:
            type: custom:mod-card
            card:
              type: custom:auto-entities
              card:
                type: grid
                square: false
                columns: 3
              filter:
                include:
                  - domain: light
                    area: Bedroom
                    options:
                      type: custom:button-card
                      template:
                        - grid_card
                        - light
                  - entity_id: media_player.bedroom_tv
                    options:
                      type: custom:button-card
                      template:
                        - grid_card
                        - tv
                      tap_action:
                        action: more-info
                  - entity_id: switch.bedroom_ac
                    options:
                      type: custom:button-card
                      template:
                        - grid_card
                exclude:
                  - entity_id: light.ceiling_1
                  - entity_id: light.ceiling_2
                  - entity_id: light.hue_play_1
                  - entity_id: light.hue_play_1_2
              card_param: cards
          office:
            type: custom:mod-card
            card:
              type: custom:auto-entities
              card:
                type: grid
                square: false
                columns: 3
              filter:
                include:
                  - domain: light
                    area: Crixle's Room
                    options:
                      type: custom:button-card
                      template:
                        - grid_card
                        - light
                  - entity_id: media_player.office_speaker
                    options:
                      type: custom:button-card
                      template:
                        - grid_card
                        - tv
                      tap_action:
                        action: more-info
                  - entity_id: switch.clem
                    options:
                      type: custom:button-card
                      template:
                        - grid_card
                      lock:
                        enabled: true
                exclude:
                  - entity_id: light.ceiling_1
                  - entity_id: light.ceiling_2
                  - entity_id: light.hue_play_1
                  - entity_id: light.hue_play_1_2
              card_param: cards
              sort:
                method: domain
                reverse: false
                numeric: false
          downstairs:
            type: custom:mod-card
            card:
              type: grid
              cards:
                - type: custom:button-card
                  entity: group.kitchen
                  template:
                    - grid_card
                - type: custom:button-card
                  entity: group.livingroom
                  template:
                    - grid_card
                - type: custom:button-card
                  entity: vacuum.rug_b
                  template:
                    - grid_card
                - type: custom:button-card
                  entity: media_player.kitchen_sonos
                  template:
                    - grid_card
                    - tv
    view_layout:
      grid-area: control
      place-self: start stretch
    card_mod:
      style: |
        ha-card {
          border-radius: 30px;
        }

  ```
</details>


# Media Card
  This card pops up when I select the main TV, and allows me to skip content and adjust volume. Below that allows me to control our Philips Sync Box and change the entertainment 
 zones right blow it. I recently added a remote too for simple ADB commands!
                     
  ![Media](https://user-images.githubusercontent.com/54859942/132930473-da620641-11dc-4cf0-95d3-e256d638f508.png)
<details>
  <summary>Code</summary>
                     
  ```
  media_player.boudoir_tv_2:  ### Must be put into lovelace-ui file with appropriate entities
    title: TV Controls
    card:
      type: entities
      entities:
        - type: custom:mini-media-player
          entity: media_player.boudoir_tv_2
          volume_stateless: true
          card_mod:
            style: |
              ha-card {
                box-shadow: none;
              }
        - type: custom:mini-media-player
          entity: media_player.sync_box
          hide:
            controls: true
            power: true
            source: true
          card_mod:
            style: |
              ha-card {
                box-shadow: none;
              }
        - type: custom:mod-card
          card:
            type: grid
            cards:
              - type: custom:button-card
                tap_action:
                  action: toggle
                entity: script.syncboxtogglevideomode
                layout: vertical
                show_name: false
                template: scene
                styles:
                  card:
                    - box-shadow: >-
                        rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px
                        3px 6px
              - type: custom:button-card
                tap_action:
                  action: toggle
                entity: script.syncboxtogglemusicmode
                layout: vertical
                show_name: false
                template: scene
                styles:
                  card:
                    - box-shadow: >-
                        rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px
                        3px 6px
              - type: custom:button-card
                tap_action:
                  action: toggle
                entity: script.syncboxtogglegamemode
                layout: vertical
                show_name: false
                template: scene
                styles:
                  card:
                    - box-shadow: >-
                        rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px
                        3px 6px
              - type: custom:button-card
                tap_action:
                  action: toggle
                entity: script.syncboxdecrease
                layout: vertical
                show_name: false
                template: scene
                styles:
                  card:
                    - box-shadow: >-
                        rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px
                        3px 6px
              - type: custom:button-card
                tap_action:
                  action: toggle
                entity: script.syncboxtoggle
                layout: vertical
                show_name: false
                template: scene
                styles:
                  card:
                    - box-shadow: >-
                        rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px
                        3px 6px
              - type: custom:button-card
                tap_action:
                  action: toggle
                entity: script.syncboxintensityincrease
                layout: vertical
                show_name: false
                template: scene
                styles:
                  card:
                    - box-shadow: >-
                        rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px
                        3px 6px
              - type: custom:button-card
                tap_action:
                  action: toggle
                entity: script.syncboxstriponly
                show_icon: false
                name: Strip Only
                template: scene
                styles:
                  card:
                    - box-shadow: >-
                        rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px
                        3px 6px
              - type: custom:button-card
                tap_action:
                  action: toggle
                entity: script.syncboxstripbars
                show_icon: false
                name: Strip + Bars
                template: scene
                styles:
                  card:
                    - box-shadow: >-
                        rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px
                        3px 6px
              - type: custom:button-card
                tap_action:
                  action: toggle
                entity: script.syncboxalllights
                show_icon: false
                name: All Lights
                template: scene
                styles:
                  card:
                    - box-shadow: >-
                        rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px
                        3px 6px
            square: false
      card_mod:
        style: |
          ha-card {
            font-family: DM Sans;
            box-shadow: none;
          }
  ```
</details>        
                     
# Floor Plan
  
  This card is my favorite because it's informative and let's me look at the entire house in a glance. Best part is that it was relatively easy to make with a bit of patience. I followed [this guide](https://community.home-assistant.io/t/floorplan-ui-with-color-synced-lights/169417) and had it working within a couple hours. The guide allows you to sync the color to match color and brightness, but I had issues with color matching not being accurate so I just match brightness.
  ![floorplan](https://user-images.githubusercontent.com/54859942/120511145-1e8e0000-c398-11eb-93af-11c22549a6e9.gif)
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

# Useful Automations

  ### Make sure you understand the code and modify as necessary!
  <details>
  	<summary>Automatic Dark Mode</summary>
  
  ```
  alias: Auto Lovelace Theme
    description: ''
    trigger:
      - platform: sun
        event: sunrise
        offset: '00:10:00'
      - platform: sun
        event: sunset
        offset: '00:10:00'
    condition: []
    action:
      - service: frontend.set_theme
        data:
          name: |
            {% if is_state('sun.sun', 'above_horizon') %}
              "Custom Light Mode"
            {% else %}
              "Custom Dark Mode"
            {% endif %}
    mode: single
  ```
  </details>
  
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
