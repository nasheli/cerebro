Mirar hardware/disco.md

Kernel tiene readahead (además del readahead del dispositivo):
Leer el parámetro:
  blockdev --getra /dev/sda
  cat /sys/block/sda/queue/read_ahead_kb
Modificar el parámetro
  blockdev --setra 512 /dev/sda
  echo "512" > /sys/block/sda/queue/read_ahead_kb

El readahead tiene como contrapartida que cada lectura tarda más.

Queue length:
cat /sys/block/sda/queue/nr_requests
Tamaño de la cola de peticiones a disco.
Un valor alto puede ser bueno porque ordena las peticiones y junta las peticiones más próximas en disco.
La desventaja es que la latencia es mayor.
