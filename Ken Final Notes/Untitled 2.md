anicolas@Junos# edit system login
anicolas@Junos# edit user archie
anicolas@Junos# set full-name "Archie Val Nicolas"
anicolas@Junos# set class super-user
anicolas@Junos# set authentication plain text-password
New password:
Confirm password:
anicolas@Junos# set system host-name Junos
anicolas@Junos# set system name-server 8.8.8.8
anicolas@Junos# set system services ssh
anicolas@Junos# set system time-zone Asia/Manila
anicolas@Junos> show system uptime | match time
