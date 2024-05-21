# Set-Up-Prometheus-Grafana-AWS
opne the aws account and teh then make the ece instsnce named as promethus server on ubuntu opearting system ,
check allow http traffic from internet
check allow the https traffic from internet

in the network settings

edit settings 

in the inbound traffic rule 
add the new security group 
add the port number 9090  name it as  prometheus

add the new security group 
add the port number 3000 named it as  graphana
add the new security group 
add the portnuber fo the 9100 named it as  node-exporter 

change the source of any security group 0.0.0.0/0 in all new security group 


launch any new target instsacne on which you want ot monitor ,on ubunu operting system, in teh network setting ->edit settings 
now in the inbound traffic rule

add the new security group 
add the port number 9100 named it as the node-exporter 

and lauch the instance


