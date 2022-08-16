to do list

delete sdwan images

download new viptela sdwan versions
integrate to eve-ng

download juniper vmx 
install to eve-ng

=========================



mkdir /opt/unetlab/addons/qemu/vtbond-19.2.3

mv viptela-edge-19.2.3-genericx86-64.qcow2 virtioa.qcow2
cd

mkdir /opt/unetlab/addons/qemu/vtedge-19.2.3

cd /opt/unetlab/addons/qemu/vtedge-19.2.3
mv viptela-edge-19.2.3-genericx86-64.qcow2 virtioa.qcow2
cd

mkdir /opt/unetlab/addons/qemu/vtsmart-19.2.3

cd /opt/unetlab/addons/qemu/vtsmart-19.2.3
mv viptela-smart-19.2.3-genericx86-64.qcow2 virtioa.qcow2
cd

mkdir /opt/unetlab/addons/qemu/vtmgmt-19.2.3

cd /opt/unetlab/addons/qemu/vtmgmt-19.2.3
mv viptela-vmanage-19.2.3-genericx86-64.qcow2 virtioa.qcow2

==================

mkdir /opt/unetlab/addons/qemu/vtbond-16.2.11

cd /opt/unetlab/addons/qemu/vtbond-16.2.11
mv hda.qcow2 virtioa.qcow2
cd

mkdir /opt/unetlab/addons/qemu/vtedge-18.4.4

cd /opt/unetlab/addons/qemu/vtedge-18.4.4
mv hda.qcow2 virtioa.qcow2
cd

mkdir /opt/unetlab/addons/qemu/vtsmart-16.2.11
cd /opt/unetlab/addons/qemu/vtsmart-16.2.11
mv hda.qcow2 virtioa.qcow2
cd

mkdir /opt/unetlab/addons/qemu/vtmgmt-16.2.11

mv hda.qcow2 virtioa.qcow2
mv hdb.qcow2 virtiob.qcow2
cd
/opt/qemu/bin/qemu-img create -f qcow2 virtiob.qcow2 100G
/opt/unetlab/wrappers/unl_wrapper -a fixpermissions


management ip

-useless maglagay ng loopback sa vpn 0 (transport) since di ito routable. di naadvertise sa omp
system ip = loopback ip = router-id ng sdwan
system ip = 10.1.1.1
loopback ip = 10.1.1.1

failover scenarios
ospf and other igp - used for L3
vrrp and hsrp - used for L2
for sdwan, best practice is to use point to point ospf

==================
vEdge

ge0/0 - ztp
transport - underlay
service - overlay
vpn 0 - 512 - treat as vrf

for cisco viptela
vpn 0 - transport
vpn 512 - management
vpn 1 - 511 - service vrf (mostly underlay)

out of the box - done
configure interfaces - done
configure vrrp - done
static routing - done
ospf - done
bgp - done

ip route 10.1.1.1 255.255.255.255 10.0.20.2
ip route 10.1.1.1 255.255.255.255 10.0.30.2


default-gateway - last resort
default route - match lahat tpos doon ipapadaan

core switch and vedge
dapat nagkikita
under area 0

ip route 10.1.1.3/32 10.0.10.1
vlan 10
10.0.0.2/30
tanggal vrrp

another vlan sa switch
vlan 11
10.0.0.10/30


vedge

vlan 11
10.0.0.9/30




vlan 10 - R2
10.0.0.0/30

vlan 11 - R1
10.0.0.8/30





