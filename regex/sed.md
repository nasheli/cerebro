http://sed.sourceforge.net/grabbag/tutorials/sedfaq.txt
Manual: http://www.semicomplete.com/blog/articles/week-of-unix-tools/day-1-sed.html

Modificar fichero directamente con sed. Cambiar 127.0.0.1 por 0.0.0.0
sed -i 's/127.0.0.1/0.0.0.0/g' /etc/mysql/my.cnf

sed -i s/"\$variable = 3"/"\$variable = 3,\n\$otra = 2"/ fichero.pp


cat file | sed s/”cosa fea”/”cosa buena”/
cat file | sed s%”/cosas/con barras”%””%  #borramos /cosas/con/barras

echo ‘blackberry:$1$YctCf123456asdUwWnBl0:9081:9000:Usuario fabricante ftp KOSA:/KOSA-FTP/blackberry/:’ | sed 's@\(.*\)\(KOSA-FTP\).*@\1\2\/:@'
Con el \1 imprimimos todo lo que esté encerrado dentro del primer paréntesis


Agregar algo al final de una cadena:
echo "hostgroups=uno,dos,tres" | sed 's@\^(hostgroups=.*\)@\1,pepe@'


Modificar el mismo fichero que se edita:
sed -i s/cambiaesto/poresto/ fichero.txt

Borrar las lineas que empiezen por #
sed -i '/^#/d' fichero

Agregar un par de líneas tras una linea que tiene 'main'
sed /etc/puppet/puppet.conf -i -e"/main/a storeconfigs = true\nstoreconfigs_backend = puppetdb"


Para trabajar con el espacio en blaco -> \s
Ej:
retry_interval                  1               ; Schedule host check retries at 1 minute intervals
Queremos:
retry_interval                  1
s/\s*;.*$//


Borrar las líneas que empiezen por #
echo -e "hola que tal\n#coemntairo\notra linea" | sed '/^#.*$/d'


Del manual de semicomplete:

Grep like: sed -n '/palabra/s' /dir/file
Grep -v like: sed -n '/palabraQueNoQuiero/!p' /dir/file

Reusar partes:
$ echo "[1381467600] SERVICE STATE: CURRENT;icaro;processes;OK;HARD;1;" | sed "s/.*CURRENT;\([a-z]*\);.*/Ha dicho: \1/"
Ha dicho: icaro

Si queremos que el resto de la cadena se mantenga sin camios, y usar la pare macheada:
$ echo "[1381467600] SERVICE STATE: CURRENT;icaro;processes;OK;HARD;1;" | sed "s/;\([a-z]*\);/;XXX\1XXX;/"
[1381467600] SERVICE STATE: CURRENT;XXXicaroXXX;processes;OK;HARD;1;


# Mostrar contenido entre dos patterns
sed -n '/WORD1/,/WORD2/p' /path/to/file

# Coger la primera linea
cat fichero | sed 1q



### DUDAS ###
"[1381467600] SERVICE STATE: CURRENT;icaro;processes;OK;HARD;1;" -> quiero cambiar processes (segundo campo tras ';') por CMDprocesses



# return group a mayúsculas
echo "group_a_master_ci_3:27017" | sed s/'group_\(\w\)_.*'/'\U\1'/
A
