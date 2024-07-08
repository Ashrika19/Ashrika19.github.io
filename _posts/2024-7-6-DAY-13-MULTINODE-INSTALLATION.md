**step1**

apt-get install -y git sudo || yum install -y git sudo

**step2**

Configure each node with a static IP. For Ubuntu edit /etc/network/interfaces:

auto ens5
iface ens5 inet static
    address 172.31.33.109
    netmask 255.255.240.0
    gateway 172.31.32.1


**step3**

Add the DevStack User

useradd -s /bin/bash -d /opt/stack -m stack
chmod +x /opt/stack

**step4**
echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack

**step5**

Set Up Ssh
Set up the stack user on each node with an ssh key for access:

mkdir ~/.ssh; chmod 700 ~/.ssh
echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCyYjfgyPazTvGpd8OaAvtU2utL8W6gWC4JdRS1J95GhNNfQd657yO6s1AH5KYQWktcE6FO/xNUC2reEXSGC7ezy+sGO1kj9Limv5vrvNHvF1+wts0Cmyx61D2nQw35/Qz8BvpdJANL7VwP/cFI/p3yhvx2lsnjFE3hN8xRB2LtLUopUSVdBwACOVUmH2G+2BWMJDjVINd2DPqRIA4Zhy09KJ3O1Joabr0XpQL0yt/I9x8BVHdAx6l9U0tMg9dj5+tAjZvMAFfye3PJcYwwsfJoFxC8w/SLtqlFX7Ehw++8RtvomvuipLdmWCy+T9hIkl+gHYE4cS3OIqXH7f49jdJf jesse@spacey.local" > ~/.ssh/authorized_keys

**step6**

Download DevStack

git clone https://opendev.org/openstack/devstack
cd devstack

**step7**
Configure Cluster Controller
The cluster controller runs all OpenStack services. Configure the cluster controller’s DevStack in local.conf:

[[local|localrc]]
HOST_IP=172.31.33.109
FIXED_RANGE=172.31.32.0/20
FLOATING_RANGE=54.225.39.96/27
LOGFILE=/opt/stack/logs/stack.sh.log
ADMIN_PASSWORD=labstack
DATABASE_PASSWORD=supersecret
RABBIT_PASSWORD=supersecret
SERVICE_PASSWORD=supersecret


**step8**

for i in `seq 2 10`; do /opt/stack/nova/bin/nova-manage fixed reserve 172.31.32.$i; done


**step9**

Fire up OpenStack:

./stack.sh

**Configure Compute Nodes**

**step1** 

Configure each node with a static IP. For Ubuntu edit /etc/network/interfaces:

auto ens5
iface ens5 inet static
    address 172.31.42.36
    netmask 255.255.240.0
    gateway 172.31.32.1



**step2**
Add the DevStack User

useradd -s /bin/bash -d /opt/stack -m stack
chmod +x /opt/stack



**step3**
echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack

**step4**

Set Up Ssh
Set up the stack user on each node with an ssh key for access:

mkdir ~/.ssh; chmod 700 ~/.ssh
echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCyYjfgyPazTvGpd8OaAvtU2utL8W6gWC4JdRS1J95GhNNfQd657yO6s1AH5KYQWktcE6FO/xNUC2reEXSGC7ezy+sGO1kj9Limv5vrvNHvF1+wts0Cmyx61D2nQw35/Qz8BvpdJANL7VwP/cFI/p3yhvx2lsnjFE3hN8xRB2LtLUopUSVdBwACOVUmH2G+2BWMJDjVINd2DPqRIA4Zhy09KJ3O1Joabr0XpQL0yt/I9x8BVHdAx6l9U0tMg9dj5+tAjZvMAFfye3PJcYwwsfJoFxC8w/SLtqlFX7Ehw++8RtvomvuipLdmWCy+T9hIkl+gHYE4cS3OIqXH7f49jdJf jesse@spacey.local" > ~/.ssh/authorized_keys

**step5**

Download DevStack

git clone https://opendev.org/openstack/devstack
cd devstack

**step6**

The compute nodes only run the OpenStack worker services. For additional machines, create a local.conf with:

[[local|localrc]]
HOST_IP=172.31.42.36 # change this per compute node
FIXED_RANGE=172.31.32.0/20
FLOATING_RANGE=52.90.71.224/28
LOGFILE=/opt/stack/logs/stack.sh.log
ADMIN_PASSWORD=labstack
DATABASE_PASSWORD=supersecret
RABBIT_PASSWORD=supersecret
SERVICE_PASSWORD=supersecret
DATABASE_TYPE=mysql
SERVICE_HOST=172.31.33.109
MYSQL_HOST=$172.31.33.109
RABBIT_HOST=$172.31.33.109
GLANCE_HOSTPORT=$172.31.33.109:9292
ENABLED_SERVICES=n-cpu,c-vol,placement-client,ovn-controller,ovs-vswitchd,ovsdb-server,q-ovn-metadata-agent
NOVA_VNC_ENABLED=True
NOVNCPROXY_URL="http://$172.31.33.109:6080/vnc_lite.html"
VNCSERVER_LISTEN=$172.31.42.36
VNCSERVER_PROXYCLIENT_ADDRESS=$172.31.42.36



step2

Fire up OpenStack:

./stack.sh