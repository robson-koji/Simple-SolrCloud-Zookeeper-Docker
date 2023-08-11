# Simple-SolrCloud-Zookeeper-Docker
One zookeeper instance, and two Solr Cloud nodes.

To test versions and environment debugging.

- Wipe volumes it doesn't start/restart
- Running as root for convenience


## To create a collection

- docker volume inspect solr1
- docker exec -it -v /path/on/host:/path/in/container solr1 bin/solr zk upconfig -n <name_for_configset> -d /path/in/container

Replace /path/on/host with the actual path on your host machine where the configset directory is located, and /path/in/container with the corresponding path inside the container where you want to mount the directory.

This will mount the host directory into the container at the specified path, allowing the bin/solr zk upconfig command to access the configset directory from the host machine.
