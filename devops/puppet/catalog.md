http://manpages.ubuntu.com/manpages/precise/en/man8/puppet-catalog.8.html

Almacenado en:
/var/lib/puppet/client_data/catalog

puppet catalog download
  en un cliente, se baja su catalog del puppetmaster y lo almacena en 
curl --cert /var/lib/puppet/ssl/certs/$(hostname).pem --key /var/lib/puppet/ssl/private_keys/$(hostname).pem --cacert /var/lib/puts/ca.pem -H 'Accept: yaml' https://puppet:8140/dsn_dev/catalog/$(hostname)
  mirar api.md

puppet catalog find CERTNAME
Retrieve the catalog for a node

Para obtener el CERTNAME
puppet cert list --all

Buscar solo los recursos tipo file:
puppet catalog select node1.inet file
  Aqui veo recursos file que no se aplican a este nodo :?

Ver que clases se aplican a cada nodo
puppet catalog select node class

Listado de las máquinas que usan este puppet master
puppet cert list --all | awk '{print $2;}' | tr -d "\"" > lista_maquinas


También podemos consultar via API-REST a puppetdb.
Mirar puppetdb-query.md


## Generar catalog en JSON para un nodo ##
puppet master --compile NombreNodo > catalog-nombrenodo.json
Quitar la primera linea del fichero ya que no será parte del JSON

## Aplicar catalog en un client ##
puppet apply --catalog catalog-client.json
