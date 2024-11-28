# homebridge-gogogate2

## [![verified-by-homebridge](https://badgen.net/badge/homebridge/verified/purple)](https://github.com/homebridge/homebridge/wiki/Verified-Plugins)

[![npm](https://img.shields.io/npm/v/homebridge-gogogate2.svg)](https://www.npmjs.com/package/homebridge-gogogate2)
[![npm](https://img.shields.io/npm/dw/homebridge-gogogate2.svg)](https://www.npmjs.com/package/homebridge-gogogate2)
[![npm](https://img.shields.io/npm/dt/homebridge-gogogate2.svg)](https://www.npmjs.com/package/homebridge-gogogate2)

[![CodeFactor](https://www.codefactor.io/repository/github/nicoduj/homebridge-gogogate2/badge/dynamicplatform)](https://www.codefactor.io/repository/github/nicoduj/homebridge-gogogate2/overview/dynamicplatform)
[![Build Status](https://travis-ci.com/nicoduj/homebridge-gogogate2.svg?branch=master)](https://travis-ci.com/nicoduj/homebridge-gogogate2)
[![Known Vulnerabilities](https://snyk.io/test/github/nicoduj/homebridge-gogogate2/badge.svg?targetFile=package.json)](https://snyk.io/test/github/nicoduj/homebridge-gogogate2?targetFile=package.json)

[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)

[![Support via PayPal][paypal-button]][paypal-nicoduj]

<img src="https://user-images.githubusercontent.com/19813688/80208881-5d984080-8631-11ea-9903-36224778c8d4.PNG" width="25%" align="right">

[Gogogate 2](https://www.gogogate.com) - old model, not iSmartGate that is natively homekit enabled - plugin for [HomeBridge](https://github.com/nfarina/homebridge) using http calls.

This plugin will add your doors connected to gogogate to homekit. It can update in the background so that openning / closing outside home app can trigger your automations. It will also display battery sensor and temperature from your wireless sensors.

## Installation

1. Install Homebridge using: `npm install -g homebridge`
2. Install this plugin using: `npm install -g homebridge-gogogate2`
3. Update your Homebridge `config.json` using the sample below.

## Configuration

```json
"platforms": [
  {
    "platform": "GogoGate2",
    "name": "GogoGate2",
    "gogogateIP": "192.168.1.47",
    "username": "",
    "password": "",
    "refreshTimer": "120",
    "maxWaitTimeForOperation": "30",
    "refreshTimerDuringOperartion": "5"
  }
]
```

Fields:

- `platform` must be "GogoGate2" (required).
- `name` is the name of the published accessory (required).
- `gogogateIP` is the static IP address of the gogogate (required). A static IP address is required.
- `username` your username for accessing the gate (must be admin)
- `password` your password
- `refreshTimer` Optional - enable refresh of doors state every X seconds, for automation purpose if you need to activate something else based on a state change of a door by another means than homekit. Be aware it might make you gogoggate smokes since the plugin will ask its status very often :) (defaults : disable, accepted range : 30-600s).
- `maxWaitTimeForOperation` Optional - set the maximum time that we wait for door operation to complete. When elapsed, check the current State again and updates accordingly. (defaults : 30s, accepted range : 30-90s).
- `refreshTimerDuringOperation` Optional - set the refresh timer during operation in progress to detect the end of the operation. (defaults : 10s, accepted range : 2-15s).
- `cleanCache` Set it to true in case you want to remove the cached accessory (only those from this plugin). You have to restart homebridge after applying the option. Remove it after restart, otherwise it will be recreated at each startup.

## Changelog

See [CHANGELOG][].

[changelog]: CHANGELOG.md

## Inspiration

Thanks to :

- [dlbroadfoot] for the API calls.
- every tester / contributor that test, and give feedback in any way !

[dlbroadfoot] https://github.com/dlbroadfoot/pygogogate2

## Donating

Support this project and [others by nicoduj][nicoduj-projects] via [PayPal][paypal-nicoduj].

[![Support via PayPal][paypal-button]][paypal-nicoduj]

[nicoduj-projects]: https://github.com/nicoduj/
[paypal-button]: https://img.shields.io/badge/Donate-PayPal-green.svg
[paypal-nicoduj]: https://www.paypal.me/nicoduj

## License

As of Dec 01 2018, Nicolas Dujardin has released this repository and its contents to the public domain.

It has been released under the [UNLICENSE][].

[unlicense]: LICENSE
