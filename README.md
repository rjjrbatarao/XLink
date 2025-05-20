[![Production](https://img.shields.io/badge/Production%3F-no-red.svg)](https://bitbucket.org/lbesson/ansi-colors) [![Alpha](https://img.shields.io/badge/Alpha%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity) [![Testing](https://img.shields.io/badge/Testing%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)

# XLink
Xlink firmware is FREE Proof Of Concept voucher and cash terminal for `TPLink EAP 1xx/2xx`, `Mikrotik` and soon any `OpenWRT` access points.
This is done by the `XLink` firmware that acts as coin and bill `Cash Terminal` for customer wifi session generation.

![image](https://github.com/user-attachments/assets/b11121dd-5844-4771-a13a-6766e4714b3a)



## Important! Requirements
- tplink eap 110 or 225 with configured ssid or mikrotik and soon openwrt
- esp32 devkit for now, soon esp32s3 n16r8 will be recommended!!
- installed serial drivers `CP2xx or CH3xx` provided above drivers folder
Note: this is 1:1 meaning 1 esp per AP so if mikrotik used you cannot add more esp32!!

## Pinout Wireless
![image](https://github.com/user-attachments/assets/9cc2a499-ce36-4a10-93ce-48d9b1ec1c7c)

| ESP32  | ESP32S3 | Description |
| - | - | - |
| 15  | 15  | COIN PIN  |
| 13  | 13  | COIN POWER CUT  |

## Components Setup Per AP
| Name  | ESP32 | EXTERNAL AP | EXTERNAL ROUTER | CLIENTS | HZ | COST | ANTITETHER | description |
| - | - | - | - | - | - | - | - | - |
| TPLink EAP110  | ✅  | ❌  | optional | 10 - 15 | 2.4G | LOW | NO? |router is required if you need ttl 1 or (antitether) for budget starter vendo| 
| TPLink EAP225   | ✅  | ❌  | optional | 20 - 40 | 2.4G + 5G | MID | NO? |router is required if you need ttl 1 or (antitether) high end| 
| Mikrotik Haplite  | ✅  | optional  | ❌ | 10 - 15 | 2.4G | LOW | YES |good with antitheter but need external AP for extending wifi range | 
| Mikrotik RBMetal  | ✅  | ❌  | ❌ | 20 - 30 | 2.4G | HIGH | YES |supports antitether but expensive | 
| Mikrotik wAP  | ✅  | ❌  | ❌ | 20 - 30 | 2.4G + 5G | MID | YES |this might be the best setup for price and frequency to avoid antitether| 
| Comfast E314n V2 Openwrt  | ✅  | ❌  | ❌ | 10 - 15 | 2.4G | LOW | YES |in openwrt setting ttl is possible so no need external router |
| Comfast CF-E73 V2 Openwrt  | ✅  | ❌  | ❌ | 10 - 15 | 2.4G | LOW | YES |in openwrt setting ttl is possible so no need external router |
| Other Openwrt  | ✅  | ❌  | ❌ | 10 - 100 | 2.4G or 5G | LOW-HIGH | YES |in openwrt setting ttl is possible so no need external router |

## Modes
Voucher generator manual: TODO\
Piso wifi vendo autologin: Implemented 

## Installation
Download XLink firmware from [RELEASE](https://github.com/rjjrbatarao/XLink/releases) or use this link [WEB INSTALLER](https://xlnk.xmachinesystems.com/)\
NOTE: Before diving into below Steps please Power up your Tplink ap and connect to dhcp source or fiber modem!! You must set the SSID!! follow this guide [GUIDE](https://www.tp-link.com/us/configuration-guides/quick_setup_guide_for_standalone_omada_eaps/?configurationId=18595#_idTextAnchor007)

## Step 1
You must have installed the drivers if com not detected, `CP2xx or CH3xx` is the keyword!!\
![image](https://github.com/user-attachments/assets/3b80596e-02b3-4977-afda-3c003596b376)

## Step 2
Click install and wait to finish in 3 to 4 minutes, and after click `Next`\
![image](https://github.com/user-attachments/assets/cb70b19c-50ea-407f-8871-17027ef9da0f)

## Step 3
Scanning network and put your TPlink ap ssid and password if required. License is not used here leave it blank.\
Note: if failed just refresh and follow 1 but in step 2 choose `Connect to Wi-Fi`\
![image](https://github.com/user-attachments/assets/bfdfe651-3502-4c68-ae31-b08eaca8646d)

## Step 4
Click `Connect` and afterwards `Visit Device`, details on this will be used later.
Popup is the External web portal save this for later use in step 5.
![image](https://github.com/user-attachments/assets/b473a422-580b-44b4-93e3-03ba5f086a4d)

## Step 5
10.5.50.220 is just example ip given by router to ESP32. If you click the `Visit Device` you will get the IP and the External web link
![image](https://github.com/user-attachments/assets/e533cde0-7f53-4ace-a75e-84bc20582bc6)
| Name  |  Description |
| - | - |
| RADIUS Server IP:  | ip of the esp32 can be aquired through the `Visit Device` or checking the tplink admin page  |
| RADIUS Password: | default is `secret123` change this later  |
| NAS ID: | any naming `eap110` is just example  |
| External Web Portal URL: | clicking the `Visit Device` will reveal this link  |


## Step 6
Follow this image and click save\
![image](https://github.com/user-attachments/assets/14814f20-5cfc-402f-95f9-5dcafbaba664)


## Api Documentation
Here we have our basic api list to change settings and pin mapping you must know how to use `POSTMAN` or `CURL` to use this method.\
CURL: [download](https://curl.se/windows/) for cli\
POSTMAN: [download](https://www.postman.com/downloads/) for graphical

### Example CURL command BASIS
```
curl -u admin:admin --header "Content-Type: application/json" \
  --request POST \
  --data '{"pin_coin":"15","pin_coin_cut":"13","pin_coin_level":"1"}' \
  http://10.5.50.220/settings
```

---
POST: /settings\
AUTH: Basic Auth\
CREDENTIALS: admin | admin\
PAYLOAD:
```json
{"pin_coin":"15","pin_coin_cut":"13","pin_coin_level":"1"}
```
CURL:
```
curl -u admin:admin --header "Content-Type: application/json" \
  --request POST \
  --data '{"pin_coin":"15","pin_coin_cut":"13","pin_coin_level":"1"}' \
  http://10.5.50.220/settings
```
---
POST: /settings\
AUTH: Basic Auth\
CREDENTIALS: admin | admin\
PAYLOAD:
```json
{"admin_username":"admin","admin_password":"admin","radius_secret":"secret123"}
```
CURL:
```
curl -u admin:admin --header "Content-Type: application/json" \
  --request POST \
  --data '{"admin_username":"admin","admin_password":"admin","radius_secret":"secret123"}' \
  http://10.5.50.220/settings
```
---
POST: /rates\
AUTH: Basic Auth\
CREDENTIALS: admin | admin\
PAYLOAD:
```json
[{"p":1,"t":5},{"p":5,"t":30},{"p":10,"t":60},{"p":20,"t":120},{"p":50,"t":300}]
```
CURL:
```
curl -u admin:admin --header "Content-Type: application/json" \
  --request POST \
  --data '[{"p":1,"t":5},{"p":5,"t":30},{"p":10,"t":60},{"p":20,"t":120},{"p":50,"t":300}]' \
  http://10.5.50.220/rates
```
NOTE: p is price and t is time in minutes

## Portal Customizations
Above is the 11kb file in portal folder for TPlink AP will be needed to modify if using mikrotik or openwrt setup.

## ISSUES and TODO
- no cleanup process yet, client accumulation could make esp32 to stop accepting new customers need to be in next release TODO
- no autopause, ongoing idle-timeout introduced on the settings and still under development TODO
- no admin panel yet we need our non technical user to configure this with friendly UI!!! TODO
- xlink stopped working due to wrong ip? the IP esp32 and the ap should be made static TODO howto
