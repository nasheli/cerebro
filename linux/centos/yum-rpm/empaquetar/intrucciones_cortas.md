# https://wiki.icinga.org/display/howtos/Build+Icinga+RPMs

yum install rpmdevtools make
/usr/sbin/useradd makerpm
su - makerpm
rpmdev-setuptree
cd rpmbuild
vim ~/.rpmmacros
Podemos definir macros del sistema (/etc/rpm/macros.dist)


Hacer un paquete desde fuentes:
vi SPECS/paquete.spec
chown makerpm:makerpm SPECS/paquete.spec
cp paquete.tar.gz /home/makerpm/rpmbuild/SOURCES/
rpmbuild -ba SPECS/icinga.spec

Paquete creado en RPMS/$architecture/
