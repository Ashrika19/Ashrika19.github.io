**OPENSTACK**

- OpenStack is a cloud computing platform that allows you to create and manage large groups of virtual machines (VMs) and other resources in a data center. Think of it as the software that lets you build your own cloud, similar to how big companies like Amazon and Google offer cloud services.

- It’s free and open source, meaning anyone can use it, modify it, and contribute to its development.

**SERVICES OF OPENSTACK**

- HORIZON(Dashboard): Provides a graphical user interface (GUI) for managing and monitoring OpenStack services.

- NOVA(Compute service): Handles instance creation, scheduling, and management of computing resources.

- GLANCE(Image service): : Simplifies VM deployment by providing a library of pre-configured images for users to launch instances from.

- KEYSTONE(Identity service): Ensures secure access control to OpenStack resources.

- NEUTRON(Networking Service): Enables communication between instances and external networks, crucial for building complex network topologies.

- CINDER(Block Storage Service):  Provides persistent block storage to VMs.

- SWIFT(Object Storage Service): Provides scalable and redundant object storage

**Additional Services (Optional and Advanced):**
- Heat (Orchestration Service): Automates the deployment of complex cloud applications using templates.

- Ceilometer (Telemetry Service): Collects and manages usage and performance data across OpenStack services.

- Trove (Database as a Service): Provides database management capabilities as a service.

- Sahara (Data Processing Service): Manages big data processing frameworks like Hadoop and Spark.

- Barbican (Key Management Service): Manages secrets and sensitive data encryption keys.

- Zaqar (Messaging Service): Provides messaging queues for applications to communicate asynchronously.

- Ironic (Bare Metal Service): Manages physical servers instead of virtual machines for specific workload requirements.

- **Keystone (Identity Service)**: Manages users and their access to different parts of the cloud.
Enables communication between instances and external networks, crucial for building complex network topologies.

- **Nova (Compute Service)**: Manages the lifecycle of virtual machines.

- **Neutron (Networking Service)**: Handles networking for virtual machines so they can communicate with each other and the internet.

- **Cinder (Block Storage Service)**: Provides additional storage that can be attached to virtual machines.

- **Swift (Object Storage Service)**: Stores and retrieves large amounts of unstructured data



**COMMANDS OF OPENSTACK**

- PROJECT

- openstack project list
- openstack project create app1

- openstack user create --domain default --password redhat shalu

- openstack domain list
 
- openstack user list
 
- openstack role list
 
- openstack role add --project demo --user shalu admin

                                                  
-   13  openstack image list
-   14  pwd
-   19  cd devstack/
-   20  source openrc
-  21  openstack image list
-   22  wget https://releases.ubuntu.com/jammy/ubuntu-22.04.4-live-server-amd64.iso
-   25  openstack image list-

-  33  openstack flavor list

-   34  openstack flavor create m1.tiny --id auto --vcpus 1 --ram 512 --disk 1 --ephemeral 0 --swap 0 --rxtx-factor 1 --public

-  35  openstack image list

-   36  sudo openstack image create "ubuntu" --disk-format iso --container-format aki --public --file /opt/stack/devstack/ubuntu-22.04.4-live-server-amd64.iso
-   37 source openrc

-   39  source openrc admin admin

-   40  sudo openstack image create "ubuntu" --disk-format iso --container-format aki --public --file /opt/stack/devstack/ubuntu-22.04.4-live-server-amd64.iso
   
-   50  source openstack_rc.sh admin admin
   
-  51  sudo openstack image create "ubuntu" --disk-format iso --container-format aki --public --file /opt/stack/devstack/ubuntu-22.04.4-live-server-amd64.iso
  
-   52  source openstack_rc.sh 
  
-   55  openstack flavor create m1.tiny --id auto --vcpus 1 --ram 512 --disk 1 --ephemeral 0 --swap 0 --rxtx-factor 1 --public
  
-   56  openstack flavor create c5.xlarge --id auto --vcpus 1 --ram 512 --disk 1 --ephemeral 0 --swap 0 --rxtx-factor 1 --public
  
-   58  cat openrc
  
-   59  openstack project create admin
  
-   61  sudo openstack project create A
  
-   62  openstack project list
  
-   63  source openrc admin demo
  
-   65  ls
  
-   66  souce openstack_rc.sh admin demo
  
-   67  source openstack_rc.sh admin demo
   
-   73  openstack volume create --size 1 myfirstvolume
   
-   74  openstack volume ls
   
-   77  cd devstack/
   
-   78  openstack subnet create --subnet-range 10.0.0.0/29 --network net1 subnet1
   
-   79  source ~/devstack/openrc admin admin
   
-   80  source openrc admin admin
   
-   81  openstack subnet create --subnet-range 10.0.0.0/29 --network net1 subnet1
  
-   82  openstack volume list
   
-   83  openstack region show
   
-   84  openstack security group list
   
-   85  openstack security group create --project admin
   
-   86  openstack security group create --project admin sg1
   
-   87  openstack security group list
   
-   88  openstack security group rule list
   
 -  89  openstack security group rule create --proto tcp --dst-port 22 sg1
   
-   90  openstack security group rule create --proto tcp --dst-port 80 sg1
   
-   91  openstack security group rule create --proto udp --dst-port 80 sg1
   
   92  openstack security group rule list sg1
-   
-   93  openstack server list
   
-  94  #openstack server create --image ubuntu --volume myfirstvolume --flavor c5.xlarge --security-group sg1 
   
-   95  openstack keypair list
   
-   96  openstack keypair create test > test.pem
   
-   97  openstack keypair list
   
-   98  #openstack server create --image ubuntu --volume myfirstvolume --flavor c5.xlarge --security-group sg1 --key-name test --availability-zone nova --network net1 
   
-   99  openstack server add port 80
  
-  100  openstack server add port -h
  
-  101  openstack server add port 80:80
  
-  102  openstack server add port 80 443
  
-  103  openstack server add port 443  443
  
-  104  openstack server create --image ubuntu --volume myfirstvolume --flavor c5.xlarge --security-group sg1 --key-name test --availability-zone nova --network net1 controller
  
-  105  openstack server create --image ubuntu  --flavor c5.xlarge --security-group sg1 --key-name test --availability-zone nova --network net1 controller
  
-  106  openstack flavour list
  
-  108* openstack server create  --flavor ds4G --security-group sg1 --key-name test --availability-zone nova --network net1 controller
  
-  109  openstack server list
  
-  110  openstack image list
  
-  111  ls
  
-  112  openstack image list
  
-  113  sudo openstack image create "ubuntu" --disk-format iso --container-format aki --public --file /opt/stack/devstack/ubuntu-20.04.6-live-server-amd64.iso 
  
-  114  source ~/devstack/openrc admin admin
  
-  115  source openrc admin admin
  
-  116* sudo openstack image create "ubuntu" --disk-format iso --container-format aki --public --file /opt/stack/devstack/ci
  
-  117  openstack server create --image cirros-0.6.2-x86_64-disk --flavor ds4G --security-group sg1 --key-name test --availability-zone nova --network net1 controller
  
- 118  openstack role add --project demo --user admin admin
  
-  119  openstack role add --project admin --user cirros cirros
  
-  120  openstack role list
  
-  121  openstack user list
  
-  122  openstack user add cirros
  
-  123  openstack user list
  
-  124* source openrc op
  
-  125  openstack role create role1
  
-  126  openstack role list
  
-  127  openstack role add --project admin --user cirros admin
  
-  128  openstack role add --project admin --user cirros adm
  
-  129  openstack user create --project admin
  
-  130  openstack user create --project admin cirros
  
-  131  openstack user list

-  132  openstack role add --project admin --user cirros admin

-  133  openstack role list

-  134  openstack role list admin

-  135  openstack role admin

-  136  openstack floating ip create public

-  137  openstack floating ip list


