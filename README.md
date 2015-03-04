# URL
https://panel.cloudatcost.com/API/v1/

# HTTP response codes
200 Success
400 Invalid API URL
403 Invalid or missing API key
412 Request failed
500 Internal server error
503 Rate limit hit

# Function list
/API/v1/clientlist
/API/v1/listservers
/API/v1/listtasks
/API/v1/listtemplates
/API/v1/poweropp
/API/v1/rebuildserver

# Standard response
Usual respose to each query:
Success:
  {
    "status": "ok",
      "time": 1425064819,
      "id": "90000",
      "data": []
  }
Error:
  {
    "status": "error",
      "time": 1425064819,
      "id": "90000"
  }

# Listservers
GET - listservers
List all servers on the account

Example:
GET https://panel.cloudatcost.com/API/v1/listservers
PARAMS 
  key = KEY
  login = example@example.com
EXAMPLE
  curl https://panel.cloudatcost.com/API/v1/listservers?key=KEY&login=example@example.com

Output:
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

# List templates
GET - listtemplates 
List all templates available

Example:
GET https://panel.cloudatcost.com/API/v1/listtemplates
PARAMS 
  key = KEY
  login = example@example.com
EXAMPLE
  curl https://panel.cloudatcost.com/API/v1/listtemplates?key=KEY&login=example@example.com

Output:
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

# Power operations
POST - poweropp 
Activate power operations

Example:
POST https://panel.cloudatcost.com/API/v1/poweropp
PARAMS
  key = KEY
  login = example@example.com
  action = poweron,poweroff,reset
EXAMPLE
  curl --data "key=KEY&login=example@example.com&action=reset" https://panel.cloudatcost.com/API/v1/poweropp

Output:

