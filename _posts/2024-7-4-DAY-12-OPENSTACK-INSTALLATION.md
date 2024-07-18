**OPENSTACK-INSTALLATION**
--------------------------------------------------------------------------------------------------------------------------------------------------------------
-    2  ll
-    3  ./stack.sh
-    4  ADMIN_PASSWORD=admin
-    5  DATABASE_PASSWORD=admin
-    6  RABBIT_PASSWORD=$admin
-    7  SERVICE_PASSWORD=$admin
-    8  apt insall net-tools
-    9  apt install net-tools
-   10  ifconfig
-   11  vim local.conf
-   12  ll
-   13  ./stack.sh
-   14  vim /etc/sudoers
-   15  ./stack.sh
-   16  ll
-   17  exit
-   18  pwd
-   19  vim /etc/nginx/nginx.conf
-   20  apt install apache2*
-   21  apt install nginx*
-   22  apt update
-   23  apt install nginx*
-   24  apt fix-update
-   25  apt install nginx
-   26  apt autoremove
-   27  apt install nginx*
-   28  vim /etc/nginx/nginx.conf
-   29  vim /etc/nginx/sites-enabled/default
-   30  systemctl restart nginx
-   31  systemctl status nginx
-   32  netstat -tunlp | grep 8080
-   33  netstat -tunlp | grep 80
-   34  ufe status
-   35  ufw status
-   36  ifconfig
-   37  openstack image list  ll
-   40  ll |grep openrc
-   41  source ~/devstack/openrc admin admin
-   42  source openrc admin admin
-   43  ll |grep openrc
-   44  openstack image list
-   45  history
-   46  ip a
-   47  vi local.conf
-   48  openstack server list
-   49  openstack project list
-   50  openstack flavor create --ram 512 --disk 1 --vcpus 1 m1.tiny
-   51  openstack flavor list 
-   52  wget https://releases.ubuntu.com/focal/ubuntu-20.04.6-live-server-amd64.iso
-   53  ll
-   54  openstack image create "ubuntu" --disk-format iso --container-format aki --public --file /opt/stack/devstack/ubuntu-20.04.6-live-server-amd64.iso
-   55  openstack image list
-   56  openstack flavor create --ram 512 --disk 1 --vcpus 4 c5.xlarge
-   57  openstack flavor list
-   58  ip netns
-   59  openstack keypair create test > test.pem
-   60  chmod 600 test.pem
-   61  openstack network create NETWORK_NAME
-   62  openstack subnet create --subnet-pool 10.0.0.0/29 --network NETWORK_NAME subnet1
-   63  openstack volume list
-   64  openstack volume create --size 1 MyFirstVolume
-   65  openstack volume list
-   66  history


- sudo ufw status

- sudo ufw enable

- sudo ufw allow 22

- source openrc admin admin
