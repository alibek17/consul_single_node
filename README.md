# consul_single_node

sudo hostnamectl set-hostname consul-instance.com --static

sudo setenforce 0

sudo sed -i 's/^SELINUX=.*/SELINUX=permissive/g' /etc/selinux/config

sudo groupadd --system consul

sudo useradd -s /sbin/nologin --system -g consul consul

sudo mkdir -p /var/lib/consul /etc/consul.d

sudo chown -R consul:consul /var/lib/consul /etc/consul.d

sudo chmod -R 775 /var/lib/consul /etc/consul.d

sudo vi /etc/hosts -> 172.31.1.67 consul-instance.com consul-01

consul keygen

config.json -> /etc/consul.d/config.json

consul validate /etc/consul.d/config.json

consul.service -> /etc/systemd/system/consul.service

sudo systemctl start consul

sudo systemctl enable consul

consul members
