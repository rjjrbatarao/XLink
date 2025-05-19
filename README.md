[![Production](https://img.shields.io/badge/Production%3F-no-red.svg)](https://bitbucket.org/lbesson/ansi-colors) [![Alpha](https://img.shields.io/badge/Alpha%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)

# XLink
Xlink firmware is a voucher and credit terminal for TPLink EAP 1xx/2xx, Mikrotik or soon any OpenWRT access points.
This is done by the XLink firmware that acts as coin and bill terminal for customer wifi access generation.

![image](https://github.com/user-attachments/assets/b11121dd-5844-4771-a13a-6766e4714b3a)



## Requirements
- tplink eap 110 or 225 with configured ssid
- esp32 devkit
- installed serial drivers

## Installation
download xlink firmware from [release](https://github.com/rjjrbatarao/XLink/releases) or use this link [installer](https://xlnk.xmachinesystems.com/)
Power up your Tplink ap and connect to internet and dhcp source You must set the SSID

## Step 1
You must have installed the drivers if com not detected, cp2xxx or chxxx is the keyword
![image](https://github.com/user-attachments/assets/3b80596e-02b3-4977-afda-3c003596b376)

## Step 2
Click install and wait to finish in 3 to 4 minutes
![image](https://github.com/user-attachments/assets/cb70b19c-50ea-407f-8871-17027ef9da0f)

## Step 3
Scan network and put your TPlink ap ssid and password if required
Note if failed just refresh and follow 1 but in step 2 choos Connect to Wi-Fi
![image](https://github.com/user-attachments/assets/bfdfe651-3502-4c68-ae31-b08eaca8646d)

## Step 4
Click Connect and Visit Device, details on this will be used later, popup will show
![image](https://github.com/user-attachments/assets/b473a422-580b-44b4-93e3-03ba5f086a4d)

## Step 5
![image](https://github.com/user-attachments/assets/c8493ce3-6a01-4e70-adf3-424926cb38de)

## Step 6
![image](https://github.com/user-attachments/assets/14814f20-5cfc-402f-95f9-5dcafbaba664)

## Pin remapping
POST: /settings
PAYLOAD:
```json
{

"pin_coin":"15",
"pin_coin_cut":"13"
}
```
## Other settings
POST: /settings
PAYLOAD:
```json
{
"admin_username":"admin",
"admin_password":"admin"
"pin_coin_level":"1"
}
```
POST: /rates
PAYLOAD:
```json
[{"p":1,"c":5},{"p":5,"c":30}]
```
