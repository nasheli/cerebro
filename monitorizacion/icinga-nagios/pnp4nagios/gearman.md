http://docs.pnp4nagios.org/pnp-0.6/config#gearman_mode

yum install pnp4nagios
  cuidado, instala nagios como dependencia, aunque no lo arranca ni pone como enabled
  rm /etc/httpd/conf.d/nagios.conf

Falta el /etc/init.d/pnp_gearman_worker

Lo podemos coger del repo oficial, pero falta poner algunos parámetros:
http://sourceforge.net/p/pnp4nagios/code/ci/master/tree/scripts/rc.pnp_gearman_worker.in?format=raw

Puestas las variables, y ejecutando con el user nagios (para que pueda escribir el pid en /var/mod_gearman por defecto):
https://gist.github.com/c8588823a9536868251b

Meterlo en el arranque:
chkconfig --add pnp_gearman_worker

[root@controller init.d]# ./pnp_gearman_worker start
Starting pnp_gearman_worker Perl module Gearman::Worker not found

Instalar perl-Gearman-Client-1.11-1.el6.0.centos.noarch.rpm (en este directorio)
https://github.com/uburu/cerebro/raw/master/monitorizacion/icinga-nagios/pnp4nagios/perl-Gearman-Client-1.11-1.el6.0.centos.noarch.rpm

yum install perl-Crypt-Rijndael

Por ultimo hacer que el fichero de passwd apunte al de icinga
Y el "AuthName" debe ser igual que el de icinga ("Icinga Access")
vi /etc/httpd/conf.d/pnp4nagios.conf


Por defecto corre como el usuario nagios.
Cambiar "USER=" en el script de init.d
Cambiar los permisos de:
  chown -R icinga.icinga /var/lib/pnp4nagios/
  chown -R icinga.icinga /var/log/pnp4nagios/
  chgrp icinga /etc/pnp4nagios/process_perfdata.cfg
  chown -R icinga.icinga /var/spool/pnp4nagios/