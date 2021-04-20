# Crixle's HA Setup
### Features
- Auto updating feed card (far left)
- Light control center that switches between rooms
- Locks & CCTV camera control/library access
- Automatic light/dark mode
- Other pages for TV/music control and sensor comparison
- Hover effects for desktop view
- Dynamic scenes that get applied through-out the day, with selector below lights
### Hardware
 - Raspberry Pi 4B 4GB
 - [Samsung 500GB SSD via USB](https://www.bestbuy.com/site/samsung-t7-500gb-external-usb-3-2-gen-2-portable-solid-state-drive-with-hardware-encryption-indigo-blue/6408298.p?skuId=6408298)
 -  [HUSBZB Usb Hub (Zigbee & Z-Wave)](https://www.amazon.com/gp/product/B01GJ826F8/ref=ppx_yo_dt_b_asin_title_o03_s00?ie=UTF8&psc=1)
 -  Phillips Hue A19 Bulbs + Hub
 -  [These cheap Zigbee bulbs that work surprisingly well](https://www.homedepot.com/p/EcoSmart-60-Watt-Equivalent-A19-Dimmable-SMART-LED-Light-Bulb-Tunable-White-2-Pack-A9A19A60WESDZ02/309683612)
 -  Amazon HD Fire 10 (2019) for wall mounted tablet, running [FullyKiosk](https://www.fully-kiosk.com/)
 -  Aqara Motion/Humidity/Temperature Sensors (Controlled without Aqara hub, instead using the HUSBZB adapter
 -  Philips Motion Sensor with ambient temperature
 -  [JHome Zigbee Smart Plugs](https://www.amazon.com/gp/product/B08K7FY2GP/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)
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
| Theme | [link](https://github.com/basnijholt/lovelace-ios-themes)

### Light Mode  
![alt text](https://github.com/crixle/homeassistant-config/blob/main/light.jpg "Light Variant")
### Dark Mode  
![alt text](https://github.com/crixle/homeassistant-config/blob/main/dark.PNG "Dark Variant")
### Light Control
Control multiple lights and devices per room all while in one card! If the globe for a room is glowing, then that means lights are on in that room. Holding down on the globe will toggle them.
![alt text](https://github.com/crixle/homeassistant-config/blob/main/lights.gif "Light Controls GIF")
