# Simple-SolrCloud-Zookeeper-Docker
One zookeeper instance, and two Solr Cloud nodes.

To test versions and environment debugging.
- Running as root for convenience
 
      docker-compose run -d

- At this point, Solr must be running in cloud mode, under Zookeeper configuration management.

      http://localhost:8983/solr/#/


## Create a collection
- docker volume inspect solrcloud_solr1. By default, Docker creates host volumes in /var/lib/docker/volumes/

        docker volume inspect solrcloud_solr1
        "Mountpoint": "/var/lib/docker/volumes/solrcloud_solr1/_data",
  
- Copy your configuration folder "conf" to host volume mounted in the path just above.
- Log into the container. Any container with a Solr instance, to upconfig configset to ZK. 

      docker exec -it -u 0 solrcloud_solr1_1 bash

- Upconfig configset
  
      bin/solr zk upconfig -n <name_for_configset> -d <host mounted volume> -z zoo1:2181

- Create a collection
  
      http://localhost:8983/solr/#/~collections

- Issue a SQL query

      http://localhost:8983/solr/#/<your_collection>/sqlquery 


## Issues
Whenever restart container, need to remove and create zookeeper volume. 
  - docker volume rm solrcloud_zoo1
  - docker volume create solrcloud_zoo1

## Follow this thread
https://issues.apache.org/jira/browse/SOLR-16131?jql=text%20~%20"Error%20loading%20class%20%27solr.SQLHandler%27"

## Hard forked from here
https://github.com/gerald-axel/SolrCloud
