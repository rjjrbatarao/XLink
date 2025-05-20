[![Production](https://img.shields.io/badge/Production%3F-no-red.svg)](https://bitbucket.org/lbesson/ansi-colors) [![Alpha](https://img.shields.io/badge/Alpha%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity) [![Testing](https://img.shields.io/badge/Testing%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)

# XLink
Xlink firmware is a  PROOF OF CONCEPT voucher and credit terminal for `TPLink EAP 1xx/2xx`, `Mikrotik` and soon any `OpenWRT` access points.
This is done by the `XLink` firmware that acts as coin and bill `Cash Terminal` for customer wifi session generation.

![image](https://github.com/user-attachments/assets/b11121dd-5844-4771-a13a-6766e4714b3a)



## Important! Requirements
- tplink eap 110 or 225 with configured ssid
- esp32 devkit
- installed serial drivers `CP2xx or CH3xx` provided above

## Pinout Wireless
![image](https://github.com/user-attachments/assets/9cc2a499-ce36-4a10-93ce-48d9b1ec1c7c)

| ESP32  | ESP32S3 | Description |
| - | - | - |
| 15  | 15  | COIN PIN  |
| 13  | 13  | COIN POWER CUT  |

## Installation
Download XLink firmware from [RELEASE](https://github.com/rjjrbatarao/XLink/releases) or use this link [WEB INSTALLER](https://xlnk.xmachinesystems.com/)\
NOTE: Power up your Tplink ap and connect to internet and dhcp source You must set the SSID follow this guide [GUIDE](https://www.tp-link.com/us/configuration-guides/quick_setup_guide_for_standalone_omada_eaps/?configurationId=18595#_idTextAnchor007)

## Step 1
You must have installed the drivers if com not detected, `CP2xx or CH3xx` is the keyword!!\
![image](https://github.com/user-attachments/assets/3b80596e-02b3-4977-afda-3c003596b376)

## Step 2
Click install and wait to finish in 3 to 4 minutes\
![image](https://github.com/user-attachments/assets/cb70b19c-50ea-407f-8871-17027ef9da0f)

## Step 3
Scanning network and put your TPlink ap ssid and password if required\
Note: if failed just refresh and follow 1 but in step 2 choos `Connect to Wi-Fi`\
![image](https://github.com/user-attachments/assets/bfdfe651-3502-4c68-ae31-b08eaca8646d)

## Step 4
Click `Connect` and afterwards `Visit Device`, details on this will be used later, popup will show\
![image](https://github.com/user-attachments/assets/b473a422-580b-44b4-93e3-03ba5f086a4d)

## Step 5
![image](https://github.com/user-attachments/assets/e533cde0-7f53-4ace-a75e-84bc20582bc6)


## Step 6
![image](https://github.com/user-attachments/assets/14814f20-5cfc-402f-95f9-5dcafbaba664)

## Pin remapping
tutorial TODO!\


## Api Documentation
POST: /settings\
AUTH: Basic Auth\
CREDENTIALS: admin | admin\
PAYLOAD:
```json
{
"pin_coin":"15",
"pin_coin_cut":"13"
"pin_coin_level":"1"
}
```
## Other settings
POST: /settings\
AUTH: Basic Auth\
CREDENTIALS: admin | admin\
PAYLOAD:
```json
{
"admin_username":"admin",
"admin_password":"admin"
"pin_coin_level":"1"
}
```
POST: /rates\
AUTH: Basic Auth\
CREDENTIALS: admin | admin\
PAYLOAD:
```json
[{"p":1,"t":5},{"p":5,"t":30},{"p":10,"t":60},{"p":20,"t":120},{"p":50,"t":300}]
```
NOTE: p is price and t is time in minutes\
