# Sonarr v4 Upcoming Media Component

This has been forked from the original [sensor.sonarr_upcoming_media](https://github.com/custom-components/sensor.sonarr_upcoming_media) by [maykar](https://github.com/maykar) to work with Sonarr v4 API changes. If using Sonarr V2 or v2, please stick to the original.

Home Assistant component to feed [Upcoming Media Card](https://github.com/ndwalters/upcoming-media-card) with
Sonarr's upcoming releases.</br>
This component does not require, nor conflict with, the default Sonarr component.</br>

### With Thanks to:
[maykar](https://github.com/maykar)</br>
[bacco007](https://github.com/bacco007)
</br>


## Installation in HACS (Custom Repositories):

1. Select HACS in Home Assistant
2. Go to any of the sections (integrations, frontend, automation).
3. Click on the 3 dots in the top right corner.
4. Select "Custom repositories"
5. Add the URL "https://github.com/ndwalters/sensor.sonarr_upcoming_media"
6. Select the category "integrations".
7. Click the "ADD" button.

**You will need to restart after installation for the component to start working.**## Manual Installation:

1. Install this component by copying [these files](https://github.com/ndwalters/sensor.sonarr_upcoming_media/tree/master/custom_components/sonarr_upcoming_media) to `/custom_components/sonarr_upcoming_media/`.
2. Install the card: [Upcoming Media Card](https://github.com/ndwalters/upcoming-media-card)
3. Add the code to your `configuration.yaml` using the config options below.
4. Add the code for the card to your `ui-lovelace.yaml`. 
5. **You will need to restart after installation for the component to start working.**

| key | default | required | description
| --- | --- | --- | ---
| api_key | | yes | Your Sonarr API key
| host | localhost | no | The host Sonarr is running on.
| port | 8989 | no | The port Sonarr is running on.
| urlbase | / | no | The base URL Sonarr is running under.
| days | 7 | no | How many days to look ahead for the upcoming sensor.
| ssl | false | no | Whether or not to use SSL for Sonarr.
| max | 5 | no | Max number of items in sensor.
</br>

**Do not just copy examples, please use config options above to build your own!**
### Sample for configuration.yaml:

```
sensor:
  - platform: sonarr_upcoming_media
    api_key: YOUR_API_KEY
    host: 127.0.0.1
    port: 8989
    days: 7
    ssl: false
    max: 10
```

### Sample for ui-lovelace.yaml:

    - type: custom:upcoming-media-card
      entity: sensor.sonarr_upcoming_media
      title: Upcoming TV
      
      
### Card Content Defaults:

| key | default | example |
| --- | --- | --- |
| title | $title | "The Walking Dead" |
| line1 | $episode | "What Comes After" |
| line2 | $release | "Mon, 10/31 9:00pm" if it's more than a week away or "Monday, 9:00pm" if it's within a week.|
| line3 | $rating - $runtime | "★ 7.8 - 45 min" |
| line4 | $number - $studio | "S06E09 - AMC"
| icon | mdi:arrow-down-bold | https://materialdesignicons.com/icon/arrow-down-bold
