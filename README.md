# Simple-SolrCloud-Zookeeper-Docker
One zookeeper instance, and two Solr Cloud nodes.

To test versions and environment debugging.

- Wipe volumes it doesn't start/restart
  - docker volume rm solrcloud_zoo1
  - docker volume create solrcloud_zoo1

- Running as root for convenience


## To create a collection

- docker volume inspect solr1
- Copy conf to container
- docker cp /var/lib/docker/volumes/solr1/zk_collection/conf/ solrcloud_solr1_1:/tmp/
- bin/solr zk upconfig -n <name_for_configset> -d /tmp/conf -z zoo1:2181

## Not working
Execute command on host to create collection in container with conf from host

- docker exec -it -v /path/on/host:/path/in/container solr1 bin/solr zk upconfig -n <name_for_configset> -d /path/in/container

Replace /path/on/host with the actual path on your host machine where the configset directory is located, and /path/in/container with the corresponding path inside the container where you want to mount the directory.

This will mount the host directory into the container at the specified path, allowing the bin/solr zk upconfig command to access the configset directory from the host machine.
