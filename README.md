# rancid-opnsense
rancid script for OPNsense firewalls

modifications to the old clogin and pfrancid scripts


To set this up (This is not a complete rancid step by step....)
1. create a user on the firewall, like rancid.... add them to the admin group
2. ssh to the firewall and remove the line with "resizewin" from .profile and .login files
3. place the opn* files in the rancid bin directory
4. add the following to rancid.types.conf \
  ##OPNsense support \
  opnsense;script;opnrancid -d=1  \
  opnsense;login;opnlogin  
  
5. set up your .cloginrc like any other device \
  EXAMPLE: \
  add autoenable firewall* 1 \
  add noenable firewall* \
  add user firewall* rancid \
  add password firewall* SomeThingReallySecure \
  add method firewall* {ssh:22}  \
  add cyphertype firewall* aes256-ctr \
  add identity firewall* $HOME/.ssh/id_rsa  <<< not neccessary if you are just using password auth 
  
  

