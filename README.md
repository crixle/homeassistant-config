# Crixle's HA Setup
I've always loved HomeKit, but it lacks functionality and integration with many of my devices so I created this dashboard to give off iOS vibes but gives me the versatility my smart home needs. </br>
</br>
**NOTE: All cards have their code provided allowing simple copy and pasting into your own dash, however most require button templates provides in the rep files. As always, replace my entities with yours otherwise cards won't work.**
### Features
- Auto updating feed card (far left)
- Light control center that switches between rooms
- Interactive dynamic floor plan
- Arlo Pro 3 camera control/library access
- Automatic light/dark mode
- Media & Sync Box Control
- Hover effects for desktop view
- Automatic light/dark mode based on sun
### Hardware
 - Raspberry Pi 4B 4GB
 - [Samsung 500GB SSD via USB](https://www.bestbuy.com/site/samsung-t7-500gb-external-usb-3-2-gen-2-portable-solid-state-drive-with-hardware-encryption-indigo-blue/6408298.p?skuId=6408298)
 -  [HUSBZB Usb Hub (Zigbee & Z-Wave)](https://www.amazon.com/gp/product/B01GJ826F8/ref=ppx_yo_dt_b_asin_title_o03_s00?ie=UTF8&psc=1)
 -  Phillips Hue A19 Bulbs + Hub
 -  [These cheap Zigbee bulbs that work surprisingly well](https://www.homedepot.com/p/EcoSmart-60-Watt-Equivalent-A19-Dimmable-SMART-LED-Light-Bulb-Tunable-White-2-Pack-A9A19A60WESDZ02/309683612)
 -  Amazon HD Fire 10 (2019) for wall mounted tablet, running [FullyKiosk](https://www.fully-kiosk.com/)
 -  Aqara Motion/Humidity/Temperature Sensors (Controlled with HUSBZB adapter, not Aqara hub)
 -  2x Philips Motion Sensor with ambient temperature
 -  Phillips Sync Box
 -  Phillips 55" Gradient Strip
 -  [JHome Zigbee Smart Plugs](https://www.amazon.com/gp/product/B08K7FY2GP/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)
<details>
  <summary>Demo</summary>
  
  ![demo](https://user-images.githubusercontent.com/54859942/120359753-0d7cba80-c2d6-11eb-9c72-adbf6a378297.gif)
</details>

<details>
  <summary>Light Mode</summary>
  
  ![Light](https://user-images.githubusercontent.com/54859942/120359952-3d2bc280-c2d6-11eb-80d7-c865913088c1.PNG)

</details>

<details>
  <summary>Dark Mode</summary>
  
  ![Dark](https://user-images.githubusercontent.com/54859942/120360001-4b79de80-c2d6-11eb-8e83-73c75f24caa5.PNG)

</details>

<details>
  <summary>HACS Addons</summary>
  
  # HACS Addons
  | Card | Link |
  | :--- | ---- |
  | Button Card | [link](https://github.com/custom-cards/button-card) |
  | Vertical Stack In Card | [link](https://github.com/custom-cards/vertical-stack-in-card) |
  | CSS Card Mod | [link](https://github.com/thomasloven/lovelace-card-mod) |
  | Layout Card | [link](https://github.com/thomasloven/lovelace-layout-card) |
  | Light Popup Card | [link](https://github.com/DBuit/light-popup-card) |
  | Browser Mod | [link](https://github.com/thomasloven/hass-browser_mod) |
  | State-Switch | [link](https://github.com/thomasloven/lovelace-state-switch) |
  | Home Feed Card | [link](https://github.com/gadgetchnnel/lovelace-home-feed-card) |
  | Mini Media Player | [link](https://github.com/kalkih/mini-media-player) |
  | Aarlo | [link](https://github.com/twrecked/lovelace-hass-aarlo) |
  | Swipe Card | [link](https://github.com/bramkragten/swipe-card) |
  | Theme | [link](https://github.com/basnijholt/lovelace-ios-themes) |
  | Paper Buttons | [link](https://github.com/jcwillox/lovelace-paper-buttons-row) |
</details>

<details>
  <summary>Light Control Card</summary>
  
  Control multiple lights and devices per room all while in one card! If the globe for a room is glowing, then that means lights are on in that room. Holding down    on the globe will toggle them. Achieved by grouping the lights by rooms into grids, then using a state-switch card based off of the URL hash. Open the link above for more info.
 
  ![lightscontrol](https://user-images.githubusercontent.com/54859942/120507947-429c1200-c395-11eb-9083-74914762acf7.gif)
  ![lightpopup](https://github.com/crixle/homeassistant-config/blob/main/lightpopup.gif)
 
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
          - type: 'custom:paper-buttons-row'
            buttons:
              - entity: group.boudoir
                name: false
                icon: 'hass:sofa-single'
                style:
                  button:
                    background: 'rgba(255,255,255,.1)'
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
                      background: 'rgba(255,255,255,.5)'
                      box-shadow: '0 0 15px rgba(255,255,255,.6)'
                tap_action:
                  action: navigate
                  navigation_path: '#boudoir'
                hold_action:
                  action: toggle
              - entity: group.bedroom
                name: false
                icon: 'hass:bed-king'
                style:
                  button:
                    background: 'rgba(255,255,255,.1)'
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
                icon: 'hass:laptop'
                style:
                  button:
                    background: 'rgba(255,255,255,.1)'
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
                icon: 'hass:stairs-down'
                style:
                  button:
                    background: 'rgba(255,255,255,.1)'
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
      - type: 'custom:mod-card'
        style: |
          ha-card {
            padding: 10px;
            background: var( --ha-card-background, var(--card-background-color, white) );
            border-radius: 30px;
            }
        card:
          type: vertical-stack
          cards:
            - type: 'custom:state-switch'
              entity: hash
              default: boudoir
              states:
                boudoir:
                  type: grid
                  cards:
                    - type: 'custom:button-card'
                      entity: light.desk_lamp
                      template:
                        - light
                        - popup
                    - type: 'custom:button-card'
                      entity: light.boudoir_ceiling_light
                      template:
                        - light
                        - popup
                    - type: 'custom:button-card'
                      entity: light.hue_play_gradient_lightstrip_1
                      template:
                        - light
                        - popup
                    - type: 'custom:button-card'
                      entity: light.nanoleaf
                      template:
                        - light-alt
                        - popup
                    - type: 'custom:button-card'
                      entity: light.standing_lamp
                      template:
                        - light
                        - popup
                    - type: 'custom:button-card'
                      entity: light.tv_bars
                      template:
                        - light
                        - popup
                bedroom:
                  type: grid
                  cards:
                    - type: 'custom:button-card'
                      entity: light.vine_lights
                      template:
                        - light-alt
                        - popup
                    - type: 'custom:button-card'
                      entity: light.bedroom_floor_lamp
                      template:
                        - light-alt
                        - popup
                    - type: 'custom:button-card'
                      entity: light.bedside_lamp
                      template:
                        - light-alt
                        - popup
                office:
                  type: grid
                  cards:
                    - type: 'custom:button-card'
                      entity: light.office_strip
                      template:
                        - light
                        - popup
                    - type: 'custom:button-card'
                      entity: light.office_lamp_1
                      template:
                        - light
                        - popup
                    - type: 'custom:button-card'
                      entity: light.desk_lamp_2
                      template:
                        - light
                        - popup
                downstairs:
                  type: grid
                  cards:
                    - type: 'custom:button-card'
                      icon: 'hass:fridge'
                      entity: group.kitchen
                      template:
                        - light-alt
                        - popup
                    - type: 'custom:button-card'
                      entity: group.livingroom
                      template:
                        - light-alt
                        - popup
                    - type: 'custom:button-card'
                      entity: vacuum.rug_b
                      template:
                        - vacuum
                      tap_action:
                        action: more-info
            - type: grid
              cards:
                - type: 'custom:button-card'
                  entity: scene.morning
                  template: scene
                - type: 'custom:button-card'
                  entity: scene.evening
                  template: scene
                - type: 'custom:button-card'
                  entity: scene.in_bed
                  template: scene
                - type: 'custom:button-card'
                  entity: scene.thinkin_of_you
                  template: scene
                  name: T.O.Y.
                - type: 'custom:button-card'
                  entity: scene.nebula
                  template: scene
                - type: 'custom:button-card'
                  entity: script.movie_mode_actions
                  name: Movie
                  tap_action:
                    action: call-service
                    service: toggle
                  template:
                    - scene
              square: false
      - type: grid
        cards:
          - type: 'custom:button-card'
            tap_action:
              action: more-info
            entity: climate.gemodule0fd7
            name: Window A/C
            template:
              - spin_animation
              - footer_card
            state:
              - value: cool
                styles:
                  state:
                    - color: '#00BFFF'
          - type: 'custom:button-card'
            entity: switch.air_purifier
            template:
              - footer_card
              - spin_animation
            state:
              - value: 'on'
                styles:
                  icon:
                    - animation: spin .5s linear infinite
        square: false
        columns: 2

  ```
</details>

<details>
  <summary>Auto Feed Card</summary>
  
  I wanted to create a feed type of card that reports any low batteries, washer/dryer states, and activity of certain entities. Also give some info like weather, time, and house temperatures.
  <img width="455" alt="feed" src="https://user-images.githubusercontent.com/54859942/120509530-95c29480-c396-11eb-8c48-7b9beff26729.png">
  ## Code
  ```
type: vertical-stack
    cards:
      - type: 'custom:button-card'
        tap_action:
          action: none
        hold_action:
          action: navigate
          navigation_path: dev2
        entity: sensor.timenew
        show_icon: false
        show_name: false
        show_state: true
        styles:
          card:
            - background: none
            - box-shadow: none
            - padding: 0
          state:
            - font-size: 50px
            - font-family: Assistant
      - type: 'custom:mod-card'
        style: |
          ha-card {
            padding: 10px;
            background: var( --ha-card-background, var(--card-background-color, white) );
            border-radius: 30px;
            }
        card:
          type: vertical-stack
          cards:
            - type: weather-forecast
              entity: weather.home_2
              show_forecast: false
              style: |
                ha-card {
                  background: rgba(255,255,255,.1);
                  box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.2);
                  font-family: Assistant;
                }
            - type: vertical-stack
              cards:
                - type: conditional
                  conditions:
                    - entity: sensor.washer
                      state: 'on'
                  card:
                    type: entities
                    entities:
                      - entity: sensor.washer_state
                        name: Washer
                        secondary_info:
                          entity: sensor.washer_remaining_time
                          prefix: 'Time Remaining: '
                          postfix: ' minutes'
                    style: |
                      ha-card {
                        background: rgba(255,255,255,.1);
                        box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.2);
                        font-family: Assistant;
                      }
                - type: conditional
                  conditions:
                    - entity: sensor.dryer
                      state: 'on'
                  card:
                    type: entities
                    entities:
                      - entity: sensor.dryer_state
                        name: Dryer
                        secondary_info:
                          entity: sensor.dryer_remaining_time
                          prefix: 'Time Remaining: '
                          postfix: ' minutes'
                    style: |
                      ha-card {
                        background: rgba(255,255,255,.1);
                        box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.2);
                        font-family: Assistant;
                      }
            - type: 'custom:auto-entities'
              card:
                type: entities
                state_color: false
                card_mod:
                  style: |
                    ha-card {
                      background: rgba(255,255,255,.1);
                      box-shadow: 0 8px 15px rgba(0,0,0,.2);
                      font-family: Assistant;
                      }
              filter:
                include:
                  - entity_id: alarm_control_panel.aarlo_base_station
                    options:
                      icon: 'hass:cctv'
                      secondary_info: last-changed
                  - name: '/[Bb]attery/'
                    state: <= 10
                    options: {}
                exclude:
                  - entity_id: sensor.rug_b_battery_level
                  - entity_id: sensor.fire_tablet_battery_level
              show_empty: false
              sort:
                method: none
            - type: grid
              cards:
                - type: sensor
                  entity: sensor.lumi_lumi_weather_temperature
                  graph: line
                  name: Boudoir
                  style: |
                    ha-card {
                      overflow: hidden;
                      background: rgba(255,255,255,.1);
                      box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.2);
                      font-family: Assistant;
                    }
                - type: sensor
                  entity: sensor.philips_motion_sensor_temperature
                  graph: line
                  name: Kitchen
                  style: |
                    ha-card {
                      overflow: hidden;
                      background: rgba(255,255,255,.1);
                      box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.2);
                      font-family: Assistant;
                    }
                - type: sensor
                  entity: sensor.lumi_lumi_weather_0a037c06_temperature
                  graph: line
                  name: Tank
                  style: |
                    ha-card {
                      overflow: hidden;
                      background: rgba(255,255,255,.1);
                      box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.2);
                      font-family: Assistant;
                    }
              square: false
            - type: 'custom:paper-buttons-row'
              buttons:
                - name: All Sensors
                  style:
                    button:
                      background: 'rgba(255,255,255,.1)'
                      border-radius: 30px
                      font-size: 20px
                      font-family: Assistant
                      padding: 7px 30px
                      box-shadow: '0px 8px 15px rgba(0, 0, 0, 0.2)'
                  tap_action:
                    action: fire-dom-event
                    browser_mod:
                      command: popup
                      title: Sensors
                      card:
                        type: 'custom:swipe-card'
                        cards:
                          - type: 'custom:vertical-stack-in-card'
                            style: |
                              ha-card {
                                background: none;
                                }
                            cards:
                              - type: history-graph
                                style: |
                                  ha-card {
                                    box-shadow: none;
                                  }
                                entities:
                                  - entity: sensor.lumi_lumi_weather_temperature
                                    name: Boudoir
                                  - entity: sensor.philips_motion_sensor_temperature
                                    name: Kitchen
                                  - entity: sensor.lumi_lumi_weather_0a037c06_temperature
                                    name: Clem's Tank
                                refresh_interval: 0
                                hours_to_show: 48
                                title: House Temperatures
                              - type: history-graph
                                style: |
                                  ha-card {
                                    box-shadow: none;
                                  }
                                entities:
                                  - entity: sensor.lumi_lumi_weather_humidity
                                    name: Boudoir
                                  - entity: sensor.lumi_lumi_weather_0a037c06_humidity
                                    name: Clem's Tank
                                hours_to_show: 48
                                refresh_interval: 0
                                title: House Humidity
                          - type: vertical-stack
                            cards:
                              - type: 'custom:vertical-stack-in-card'
                                style: |
                                  ha-card {
                                    background: none;
                                    }
                                cards:
                                  - type: 'custom:button-card'
                                    entity: sensor.pot_plant_sensor_battery
                                    show_state: true
                                    name: Pot Plant
                                    layout: icon_name_state2nd
                                    icon: 'hass:cannabis'
                                  - type: horizontal-stack
                                    cards:
                                      - type: gauge
                                        entity: sensor.pot_plant_temperature
                                        min: 0
                                        max: 100
                                        name: Temperature
                                        severity:
                                          green: 70
                                          yellow: 60
                                          red: 58
                                      - type: gauge
                                        entity: sensor.pot_plant_humidity
                                        min: 0
                                        max: 100
                                        name: Humidity
                              - type: 'custom:mod-card'
                                style: |
                                  ha-card {
                                    padding: 10px;
                                    background: var( --ha-card-background, var(--card-background-color, white) );
                                  }
                                card:
                                  type: vertical-stack
                                  cards:
                                    - type: 'custom:button-card'
                                      tap_action:
                                        action: more-info
                                      entity: switch.clem
                                      icon: 'fas:dragon'
                                      layout: icon_name_state2nd
                                      show_state: true
                                      show_last_changed: true
                                      name: Clem's Tank
                                      styles:
                                        card:
                                          - background: none
                                          - box-shadow: none
                                    - type: grid
                                      columns: 2
                                      cards:
                                        - type: sensor
                                          entity: >-
                                            sensor.lumi_lumi_weather_0a037c06_temperature
                                          graph: line
                                          style: |
                                            ha-card {
                                              background: none;
                                              box-shadow: none;
                                              }
                                          name: Temperature
                                        - type: sensor
                                          entity: >-
                                            sensor.lumi_lumi_weather_0a037c06_humidity
                                          graph: line
                                          name: Humidity
                                          detail: 1
                                          style: |
                                            ha-card {
                                              background: none;
                                              box-shadow: none;
                                              }
                                      square: true
                          - type: 'custom:vertical-stack-in-card'
                            style: |
                              ha-card {
                                background: none;
                                }
                            cards:
                              - type: 'custom:button-card'
                                tap_action:
                                  action: more-info
                                entity: binary_sensor.pi_hole
                                icon: 'hass:pi-hole'
                                show_state: true
                                show_last_changed: true
                                layout: icon_name_state2nd
                                styles:
                                  state:
                                    - padding: 15px
                              - type: history-graph
                                entities:
                                  - entity: sensor.pihole_cpu_usage
                                    name: CPU
                                  - entity: sensor.pihole_memory_use
                                    name: Memory
                                  - entity: sensor.pihole_temperature
                                    name: Temperature
                                hours_to_show: 48
                                refresh_interval: 0
                              - type: glance
                                entities:
                                  - entity: sensor.pi_hole_ads_blocked_today
                                    name: Blocked Today
                                show_name: true
            - type: 'custom:home-feed-card'
              show_empty: false
              more_info_on_tap: true
              state_color: true
              compact_mode: true
              include_history: true
              style: |
                ha-card {
                  background: rgba(255,255,255,.1);
                  font-family: Assistant;
                  margin-top: 5px;
                  border-radius: 30px;
                  box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.2);
                  }
              entities:
                - entity: vacuum.rug_b
                  content_template: |
                    {{friendly_name}} {{state}}
                - entity: lock.front_door
                  content_template: |
                    {{friendly_name}} {{state}}
                - entity: lock.back_door
                  content_template: |
                    {{friendly_name}} {{state}}
                - entity: alarm_control_panel.aarlo_base_station
                  content_template: |
                    {{friendly_name}} {{state}}
                - entity: sensor.last_boot
                  icon: 'hass:home-assistant'
                  name: Last Restarted
                - entity: group.kitchen
                  name: Kitchen Lights
                  content_template: |
                    Kitchen Lights {{state}}

  ```

</details>

<details>
  <summary>Media Card</summary>
  This is just a simple card made of two cards which allows me to adjust volume and skip content on my Chromecast, and on the bottom adjust my Philips Sync Box's      modes and brightness without using their app. The card will switch to our bedroom TV if the bedroom is selected on the light control card. Note: The shortcuts on the sync box are activating scripts which just run services. Can be easily achieved by just calling the service within the button, but I'm just too lazy to go back and rewrite it.
                     
  <img width="418" alt="Screen Shot 2021-06-02 at 12 17 56 PM" src="https://user-images.githubusercontent.com/54859942/120516291-2ef4a980-c39d-11eb-8bac-ba86cd85edb7.png">
                     
  ```
type: 'custom:state-switch'
    entity: hash
    default: boudoir
    transition: swap-right
    transition_time: 250
    states:
      bedroom:
        type: 'custom:mini-media-player'
        entity: media_player.bedroom_tv
        volume_stateless: true
        artwork: material
        name: Bedroom TV
      boudoir:
        type: 'custom:mod-card'
        style: |
          ha-card {
            background: var( --ha-card-background, var(--card-background-color, white) );
            padding: 7px;
            border-radius: 30px;
            }
        card:
          type: vertical-stack
          style: |
            ha-card {
              box-shadow: 0 8px 15px rgba(0,0,0,.2)
          cards:
            - type: 'custom:mini-media-player'
              group: false
              entity: media_player.boudoir_tv_2
              artwork: material
              volume_stateless: true
              toggle_power: false
            - type: 'custom:mini-media-player'
              hide:
                controls: true
                power: true
                icon: true
              shortcuts:
                hide_when_off: true
                columns: 3
                align_text: center
                buttons:
                  - type: script
                    id: script.syncboxtogglevideomode
                    icon: 'hass:video'
                  - type: script
                    id: script.syncboxtogglemusicmode
                    icon: 'hass:music'
                  - type: script
                    id: script.syncboxtogglegamemode
                    icon: 'hass:google-controller'
                  - type: script
                    id: script.syncboxdecrease
                    icon: 'mdi:chevron-double-left'
                  - type: script
                    id: script.syncboxtoggle
                    icon: 'mdi:circle-double'
                  - type: script
                    id: script.syncboxintensityincrease
                    icon: 'mdi:chevron-double-right'
              entity: media_player.sync_box
              group: true

  ```
</details>        
                     
<details>
  <summary>Floor Plan Card</summary>
  
  This card is my favorite because it's informative and let's me look at the entire house in a glance. Best part is that it was relatively easy to make with a bit of patience. I followed [this guide](https://community.home-assistant.io/t/floorplan-ui-with-color-synced-lights/169417) and had it working within a couple hours. The guide allows you to sync the color to match color and brightness, but I had issues with color matching not being accurate so I just match brightness.
  ![floorplan](https://user-images.githubusercontent.com/54859942/120511145-1e8e0000-c398-11eb-93af-11c22549a6e9.gif)
  ## Code
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
<details>
  <summary>Auto Light/Dark Mode Automation</summary>
  
  ### Make sure you replace the themes with yours!
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
              ios-custom-light-mod
            {% else %}
              ios-dark-mode-blue-red-alternative
            {% endif %}
    mode: single
  ```

</details>
