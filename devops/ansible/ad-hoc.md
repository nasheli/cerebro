Configurar el /etc/ansible/hosts con algunos nodos, debemos tener acceso ssh.

Probamos la conectividad (ejecutamos el modulo ping):
ansible all -m ping

Podemos probar algun grupo en particular
ansible dbservers -m ping

También podemos usar un pattern
ansible web*.example.com -m ping

Ejecutar comandos en la shell
ansible host -m shell -a "pwd"
ansible localhost -m shell -a "dpkg -l ansible | grep trusty"


Si no se pone nada usa el modulo command
ansible host -a "pwd"

Ejecutar el módulo copy localmente (copia los ficheros de /tmp/ansible1/ a /tmp/ansible2/) Cuidado con las barras (/), puede copiar un dir dentro del otro.
ansible localhost -m copy -a "src=/tmp/ansible1/ dest=/tmp/ansible2/"

-C, --check	don't make any changes; instead, try to predict some of the changes that may occur

--list-hosts 	outputs a list of matching hosts; does not execute anything else
