config
system
 system-ip 1.1.1.1
 site-id 1000
 organization-name "sdwan-testlab"
 vbond 172.16.255.2
!
vpn 0
 no interface eth0
 interface eth1
  ip address 172.16.255.1/24
  tunnel-interface
  !
  no shutdown
 !
vpn 512
  interface eth0
  ip dhcp-client
  no shutdown
!
commit and-quit
!





vbond | 192.168.10.100
vmanage | vpn0 | 192.168.10.10


pag gusto mo magnetwork track, yung CCNA yung literal na headturner ni HR. Pag meron ka nyan, malaki na chance mong mainvite sa technical interview...

Once CCNA ka na, madami ka nang pagppiliang tracks. Pwede kang pumunta sa cloud (azure and aws), switching (aruba, arista), security (palo alto, fortinet,sophos), cybersec (penetration testing, red and blue teaming), devops (network automation design), sysad (linux, windows), sdwan (silverpeak, cisco viptela) etc.

mas marami ka nang options kung saan mo gustong pumasok

ang ginawa ko dati, habang wlang call, binatak ko yung ccna para lang makapasa, tapos apply apply.. matik headturn agad, lalo na taga GT ka tas may CCNA