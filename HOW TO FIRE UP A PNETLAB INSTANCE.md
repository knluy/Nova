### HOW TO FIRE UP A PNETLAB INSTANCE ON GOOGLE CLOUD PLATFORM


1. Create an account on Google Cloud Platform
![[Tech/CCNA/Images/Pasted image 20220923125002.png]]

2. Once done, create an image provided below and create a VM afterwards:

https://pnetlab.com/pages/documentation?slug=how-to-deploy-pnetlab-box-on-google-cloud

`gcloud compute images create **nested-ubuntu-xenial** --source-image-family=ubuntu-1804-lts --source-image-project=ubuntu-os-cloud --licenses https://www.googleapis.com/compute/v1/projects/vm-options/global/licenses/enable-vmx`

![[Tech/CCNA/Images/Pasted image 20220923125324.png]]

use the  following configuration

CPU: Intel
RAM - high mem (around 32GB)

Security
turn off vTPM and integrity monitoring

![[Tech/CCNA/Images/Pasted image 20220923125157.png]]


allow http and https traffic
![[Tech/CCNA/Images/Pasted image 20220923125139.png]]


When you create the vm turn off these settings as shown in image

Shielded VM
Secure Boot = Off
vTPM = Off
Integrity Monitoring = Off

———————————————————
Run this before PNETLab installation

echo "nameserver 8.8.8.8" > /etc/resolv.conf

————————————————————
And make the interface look like this

The primary network interface
iface eth0 inet manual
auto pnet0
iface pnet0 inet dhcp
    pre-up ip link set dev eth0 up
    dns-nameservers 8.8.8.8
    bridge_ports eth0
    bridge_stp off

- then proceed with the link above for the remaining config
- use sudo -i passwd to change root password

for NAT configuration, please use this link

https://www.jagchanna.ca/deploying-eve-ng-on-gcp-part3/

