http://docs.icinga.org/icinga2/latest/doc/module/icinga2/chapter/getting-started#getting-started
Mirar ansible.md

Ubuntu:
Icinga ppa: https://launchpad.net/~formorer/+archive/ubuntu/icinga
add-apt-repository ppa:formorer/icinga
apt-get update
apt-get install icinga2


RedHat:
http://packages.icinga.org/epel/
rpm --import http://packages.icinga.org/icinga.key
wget http://packages.icinga.org/epel/ICINGA-release.repo -O /etc/yum.repos.d/ICINGA-release.repo
yum makecache
yum install icinga2
# Instalar checks basicos (metiendo EPEL)
rpm -Uvh "http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm"
yum install nagios-plugins-disk nagios-plugins-ping nagios-plugins-users nagios-plugins-ssh nagios-plugins-procs nagios-plugins-swap nagios-plugins-load nagios-plugins-http

service icinga2 start
Activado por defecto en el arranque (para desactivar: chkconfig icinga2 off)

RHEL 7:
systemctl enable icinga2
systemctl start icinga2


Por defecto se instalan las siguientes features:
checker for executing checks
notification for sending notifications
mainlog for writing the icinga2.log file

Podemos chequear las activas con (RHEL, paquete icinga2-bin)
icinga2-enable-feature

A mano:
ls /etc/icinga2/features-enabled




## Por código fuente ##
https://git.icinga.org/?p=icinga2.git;a=blob;f=INSTALL;hb=HEAD

Primero crearemos los .deb y luego existe ya el metapaquete para instalar todo (https://git.icinga.org/?p=icinga2-debian.git;a=summary)

Para ubuntu/debian:
apt-get install make build-essential libssl-dev libboost-all-dev doxygen libmysqlclient-dev python-dev automake autoconf libtool libltdl-dev bison flex
Nos bajamos un snapshot del codigo en .tar.gz  (https://git.icinga.org/?p=icinga2.git;a=tree;hb=HEAD)


tar zxvf icinga2-HEAD.tar.gz
cd icinga2/
./configure -> no puedo hacerlo!! que pasa??
Note: The Git repository does not contain any auto-generated Autotools files, i.e. there is no 'configure' script. In this case you will need to regenerate the 'configure' script by running 'autogen.sh'. However, as an end-user you should reconsider whether you really want to use the code from the Git repository. In general it is advisable to use one of the dist tarballs instead.

Hay paquetes rpm generados automáticamente cada día:
http://packages.icinga.org/epel/6/snapshot/x86_64/


Al final he optado por vagrnat + autoprovision:
cd icinga2/
vagrant up
localhost:8080/icinga


La intento poner en AWS
La instalacion con el bootstrap.sh va perfecta
