# GadgeteerZA Home Assistant
A repository of the YAML files used to configure my Home Assistant instance.

<img src="images/dashboard-screenshot.jpg" width="500">

## Description
These are the YAML config files from my own installation of Home Assistant. Every installation is unique, and built up from others' ideas and code, and mine will likely be expanding and updating over time. So I will share what I've been learning on my journey, in the hope it helps other new users. I've battled up to three or four hours sometimes to just get one card working properly, and it often comes down to syntax or formatting issues.

A key focus is on the Modbus TCP interface with a Victron slar system, with a BalanceCell battery. This instance of HA is running in a Docker container (docker-compose.yaml also included).

This is not a 'how-to' guide, but intended more as a reference for others to learn from the syntax and formatting of the code, or for accessing Victron or Balancell battery Modbus address registers.

You can watch a video at https://www.youtube.com/watch?v=dlvlhou70VA about my initial setup of the dashboards.

## Key features and Integrations
The following are some notable features that thjis particular installation uses
* Modbus TCP interface to a Victron CCGX with a Multiplus II inverter/charger, and SmartSolar charger
* BalanceCell battery stats read - https://balancell.com/products/balancell-p26-solar/
* Gauges tuned for severity colours
* Ellies Efergy Engage hub energy monitoring - https://engage.efergy.com/
* Tasmota firmware on Sonoff WiFi switch via MQTT showing power usage stats, and switch control
* Glances performance stats from two servers
* Reolink WiFi IP cameras
* Apple iPhone and iPad status, location, etc
* Ambient weather station
* Weather Underground Personal Weather Station stats
* City of Cape Town load shedding
* Ring doorbell
* Google Cast for voice outputs
* Asus router for alerting VoIP phone left network (battery is flat)
* UptimeRobot to monitor key websites
* AdGuard Home for performance of DNS
* Domain name certificate expiries
* OurGroceries application (trouble showing lists though)
* Google Calendar showing next few days' schedule
* Mini graph showing actual solar charger yield comparted to weather station's actual measured radiation in W/m2, and adjusted for panel area and wattage. Also includes forecasted solar for the day.
* Restrictions set with warnings before some switches are toggled on the dashboard
* Home Assistant Community Store (HACS) integrations and frontend UI
* HA running in a Docker container

## Automations
* Voice alerting to start of rain (to take washing off the line) - unfortunately weather station takes a few minutues to report
* Voice notification to home speaker for when I leave the shopping mall
* Slider to set minimum state of charge back to Victron CCGX ESS
* Ajust minimum SoC slider to match any changes made on Victron CCGX side
* Alerts when hot water cylinder reached temperature and is ready, based on timers looking at grid power usage dropping after 10 minutes
* VoIP phone battery flat by checking when it's 'last_activity' is longer than 10 minutes ago
* Ham radio APRS beacon going offline (can't use left Zone as coordinates never change to elsewhere) so looks at a status change to 'Away' for longer than 31 minutes
* Some audio message alerts for Victron system alarms

## Files
* File in docker sub-folder is the docker-compose file I used to create the Home Assistant container
* Other config files are inside the ha-configs subfolder for HA. All are as named. The lovelace file is a copy of the Lovelace dashboard UI config to see how the UI cards are configured, especially those with text replacement for numerical value data.

## ToDo Wishlist
* Tweak load shedding card to show attributes and better status
* Try link for click on Glances card to open full Glances web page
* Automations for motion detected on cameras
* Automation to adjust battery minimum SoC based on next day's weather forecast
* Get Ambient weather card to show rain in mm instead of inches
* Integration with Geyserwise hot water cylinder heating - no comms so may need a Geyserwise Max IoT device instead
* Integration with Texecom burglar alarm system if possible 

## Credits
Some resources I learnt a lot from include:
* Video using Modbus-TCP at https://youtu.be/giosYremoss
* Modbus guide on Victron site at https://community.victronenergy.com/questions/78971/home-assistant-modbus-integration-tutorial.html and mentions automating SOC according to weather
* Another Modbus guide inc Unit ID's = https://www.reddit.com/r/homeassistant/comments/nzimbj/tutorial_how_to_integrate_a_victron_inverter_into/
* Modbus code with Victron Github code at https://github.com/lucode/home-assistant
* MQTT guide at https://www.imval.tech/index.php/blog/victron-mqtt-server-bridging
* Victron CCGX Modbus TCP FAQ at https://www.victronenergy.com/live/ccgx:modbustcp_faq
* How to set up Automations - https://youtu.be/2tRZ_WA8Xyc
* Instructions for container use of HAC - https://hacs.xyz/docs/setup/download
* HAC Custom button possibility at https://github.com/custom-cards/button-card
* RGB colour chart - https://www.rapidtables.com/web/color/RGB_Color.html
* Restriction card confirmation at https://smarthomepursuits.com/how-to-create-a-lovelace-restriction-card-in-home-assistant/
* Home Assistant docker image at https://www.home-assistant.io/installation/linux#docker-compose
