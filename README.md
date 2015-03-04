#Description
Cloud at Cost API

Information and power operations.

# URL
https://panel.cloudatcost.com/api/v2/

# Instructions
1. Sign into your account at https://panel.cloudatcost.com
2. Click 'settings'
3. Generate an api key and insert IP information into your account settings
4. Use curl to access the panel api via the IP documented as well as key and login username/email

# HTTP response codes
```
200 Success
400 Invalid api URL
403 Invalid or missing api key
412 Request failed
500 Internal server error
503 Rate limit hit
```

# Function list
```
/api/v2/listservers
/api/v2/listtemplates
/api/v2/listtasks
/api/v2/poweropp
```

# Standard response
Usual respose to each query:

Success:
```json
{
  "status": "ok",
    "time": 1425064819,
    "id": "90000",
    "data": []
}
```

Error:
```json
{
  "status": "error",
    "time": 1425064819,
    "id": "90000"
}
```

## List servers
List all servers on the account

REQUEST

GET https://panel.cloudatcost.com/api/v2/listservers

PARAMS 

key = KEY

login = example@example.com

EXAMPLE
```
curl https://panel.cloudatcost.com/api/v2/listservers?key=KEY&login=example@example.com
```
Output:
```json
{
  "status": "ok",
    "time": 1425064819,
    "id": "90000",
    "data": [
    {
      "id": "2402939",
      "CustID": "90001",
      "packageid": "21579",
      "servername": "localhost",
      "label": "api-test",
      "vmname": "c90001-iOD-848113",
      "ip": "1.2.3.4",
      "netmask": "255.255.255.0",
      "gateway": "1.2.3.1",
      "hostname": "c9000-iOD-123.cloudatcost.com",
      "rootpass": "password",
      "vncport": "45148",
      "vncpass": "vnc_pass",
      "servertype": "Custom",
      "template": "Microsoft Windows 7 (64-bit)",
      "cpu": "4",
      "cpuusage": "261",
      "ram": "4096",
      "ramusage": "3556.202",
      "storage": "69",
      "hdusage": "0.000434688",
      "sdate": "01\/26\/2014",
      "status": "Powered On",
      "panel_note": "",
      "mode": "Normal",
      "uid": "619712052",
      "sid": "240294"
    }
  ]
}
```

## List templates
List all templates available

REQUEST

GET https://panel.cloudatcost.com/api/v2/listtemplates

PARAMS 

key = KEY

login = example@example.com

EXAMPLE
```
curl https://panel.cloudatcost.com/api/v2/listtemplates?key=KEY&login=example@example.com
```
Output:
```json
{
  "status": "ok",
    "time": 1425326406,
    "data": [
    {
      "id": "26",
      "detail": "CentOS-7-64bit"
    },
    {
      "id": "27",
      "detail": "Ubuntu-14.04.1-LTS-64bit"
    },
    {
      "id": "15",
      "detail": "CentOS 6.5 64bit (LAMP)"
    },
    {
      "id": "21",
      "detail": "Ubuntu 12.10 64bit"
    },
    {
      "id": "23",
      "detail": "Ubuntu 12.04.3 LTS 64bit"
    },
    {
      "id": "24",
      "detail": "Windows 2008 R2 64bit (BigDogs Only)"
    },
    {
      "id": "25",
      "detail": "Windows 2012 R2 64bit (BigDogs Only)"
    },
    {
      "id": "14",
      "detail": "CentOS 6.5 64bit (cPanel-WHM)"
    },
    {
      "id": "13",
      "detail": "CentOS 6.5 64bit"
    },
    {
      "id": "10",
      "detail": "CentOS 6.5 32bit"
    },
    {
      "id": "3",
      "detail": "Debian 7.1 64bit"
    },
    {
      "id": "9",
      "detail": "Windows7 64bit (BigDogs Only)"
    },
    {
      "id": "2",
      "detail": "Ubuntu-13.10-64bit"
    },
    {
      "id": "1",
      "detail": "CentOS 6.4 64bit"
    },
    {
      "id": "28",
      "detail": "Minecraft-CentOS-7-64bit"
    }
  ]
}
```
## List tasks
List all tasks in operation

REQUEST

GET https://panel.cloudatcost.com/api/v2/listtasks

PARAMS 

key = KEY

login = example@example.com

EXAMPLE
```
curl https://panel.cloudatcost.com/api/v2/listtasks?key=KEY&login=example@example.com
```
Output:
```json
{
  "status": "ok",
    "time": 1425504688,
    "api": "v2",
    "cid": "734103810",
    "action": "listtasks",
    "data": [
    {
      "cid": "734103810",
      "idf": "8548136390745",
      "serverid": "0",
      "action": "reset",
      "status": "completed",
      "starttime": "1425504093",
      "finishtime": "1425504094"
    },
    {
      "cid": "734103810",
      "idf": "2268428551033",
      "serverid": "254513205",
      "action": "reset",
      "status": "pending",
      "starttime": "1425504295",
      "finishtime": "1425504312"
    }
  ]
}
```

## Power operations
Activate server power operations

REQUEST

POST https://panel.cloudatcost.com/api/v2/poweropp

PARAMS

key = KEY

login = example@example.com

sid = SERVERID

action = poweron,poweroff,reset

EXAMPLE
```
curl --data "key=KEY&login=example@example.com&sid=12345&action=reset" https://panel.cloudatcost.com/api/v2/poweropp
```

Output:

Success:
```json
{
  "status": "ok",
    "time": 1425504815,
    "api": "v2",
    "serverid": "254513205",
    "action": "reset",
    "taskid": 700420024805,
    "result": "successful"
}
```

Unsucessful:
```json
{
  "status": "error",
    "time": 1425505065,
    "error": 105,
    "error_description": "task already running"
}
```
#TODO
Metric information
