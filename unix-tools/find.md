Haz un grep en los ficheros que terminen en .cfg y muestra el nombre y la línea donde se he encontrado el match

find . -iname "*.cfg" -exec grep -Hn "RHN Satellite Web Service Check" '{}' \;

-H, --with-filename
              Print the file name for each match.  This is the default when there is more than one file to search.
-n, --line-number
              Prefix each line of output with the 1-based line number within its input file.  (-n is specified by POSIX.)


Busca con expresion regular casi insensitive
Busco ficheros que terminen con uno o mas numeros
find . -iregex ".+[0-9]+$" -type f


Nos hace un resumen de los tipos de ficheros que tenemos en este directorio y sus subdirectorios
find . -exec file {} \; | grep -o ":[^,]*" | sort | uniq -c | sort -nr


Nos dice el tamaño de los ficheros y directorios analizando tres niveles. Para encontrar que es lo que ocupa el disco duro
find . -maxdepth 3 -exec du -h {} \; | sort -hr | uniq | head -20

Buscar ficheros que no acaben en .cfg
find . ! -iregex ".*\.cfg$" -type f


Borrar los ficheros más antiguos de 30 días
find . -mtime +30 -exec rm {} \;

Buscar ficheros modificados hace menos de 5 minutos
find . -mmin -5


Busca en los ficheros que terminen en .txt dentro de /tmp la palabra "cosa".
Nos devuelve el fichero matcheado (-H) y el número de línea (-n)
find /tmp -name "*.txt" -exec grep -Hn cosa {} \;

Buscar solo en el sistema de ficheros actual (por ejemplo, no buscar en /var/log)
find /var -mount

Return code 1 si no se encuentra nada:
find directorio -mmin -1 | egrep ".*"

Si encuentra algun fichero, ejecuta el comando
find directorio -mmin -1 | egrep ".*" && comando
