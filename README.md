# snarkOS_as_service
Simple way of making snarkOS run as a service on ubuntu

## 1. Follow guidelines on installing snarkOS. 
I use the ubuntu installer. 

## 2. Create or copy over the service file. 
I have it located under ´/etc/systemd/system/´


You can also just create the file like `sudo nano /etc/systemd/system/snarkos.service`


Run `sudo systemctl daemon-reload`

## 3. Create or copy over the config file so you don't need to change/reload the systemd files (it reads this conf file instead) 

I have it located under `/opt/aleo/system/`


You can also just create the file like `sudo nano /opt/aleo/conf`

## Usefull command to start, stop and check status as well as check the logs

´sudo systemctl start snarkos.service´


`sudo systemctl stop snarkos.service`


`sudo systemctl status snarkos.service`


`journalctl -u snarkos.service -f`


´journalctl -u snarkos.service | tail -n100´
