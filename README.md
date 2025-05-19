[![Production](https://img.shields.io/badge/Production%3F-no-red.svg)](https://bitbucket.org/lbesson/ansi-colors) [![Alpha](https://img.shields.io/badge/Alpha%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)

# XLink
Xlink firmware is a voucher and credit terminal for TPLink EAP 1xx/2xx, Mikrotik or OpenWRT access points.
This is done by the XLink firmware that acts as coin and bill terminal for end users access generation.


## Requirements
- tplink eap 110 or 225
- esp32 devkit
- installed serial drivers

## Installation
download xlink firmware from release or use this link [installer](https://xlnk.xmachinesystems.com/)

## Pinremapping
```json
{

"pin_coin":"15",
"pin_coin_cut":"13"
}
```
## Other settings
```json
{
"admin_username":"admin",
"admin_password":"admin"
"pin_coin_level":"1"
}
```
