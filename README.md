# snarkOS_as_service
Simple way of making snarkOS run as a service on ubuntu


sudo nano /etc/systemd/system/snarkos.service

[Unit]
Description=snarkos
After=network.target

[Service]
EnvironmentFile=/opt/aleo/conf
ExecStart=/opt/aleo/snarkOS/target/release/snarkos start $ARGS 

Restart=always
RestartSec=10

LimitNOFILE=1024000:1024000
LimitNPROC=1024000:1024000

User=aleo
Group=aleo

[Install]
WantedBy=multi-user.target

sudo nano /opt/aleo/conf
ARGS='--node 38.140.111.236:4133  --nodisplay --prover APrivateKey1zkpF6QnL1Pty6MAFvStWvhGznuvks7KPsGyX16v6axasQ4P'

sudo systemctl daemon-reload
sudo systemctl list-timers

sudo systemctl start snarkos.service
sudo systemctl stop snarkos.service
sudo systemctl status snarkos.service
journalctl -u snarkos.service -f
journalctl -u snarkos.service | tail -n100
