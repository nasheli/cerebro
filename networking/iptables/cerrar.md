Tirar paquetes entrantes al puerto 80/TCP
iptables -A INPUT -p tcp --dport 80 -j DROP

Tirar paquetes entrantes al puerto 53/UDP de la IP 192.168.0.5 por la interfaz eth0
iptables -A INPUT -i eth0 -p udp --dport 53 -s 192.168.0.5 -j DROP


Source port
--sport

Destination ip
-d IP



No permitir conexiones desde el host 192.168.0.5:
iptables -A INPUT -s 192.168.0.5 -j DROP




-j DROP
-j REJECT
As a general rule, use REJECT when you want the other end to know the port is unreachable' use DROP for connections to hosts you don't want people to see.
http://serverfault.com/questions/157375/reject-vs-drop-when-using-iptables


Si queremos que una máquina (con MAC 00:50:56:a2:4f:4f) ni si quiera pueda obtener nuestra IP mediante una peticion ARP:
arptables -A IN -z 00:50:56:a2:4f:4f -j DROP