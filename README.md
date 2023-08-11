# Simple-SolrCloud-Zookeeper-Docker
One zookeeper instance, and two Solr Cloud nodes.

To test versions and environment debugging.
- Running as root for convenience
  
       docker-compose run -d


## To create a collection
- docker volume inspect solr1
- Copy conf to host container, mounted at the container- 
- bin/solr zk upconfig -n <name_for_configset> -d <conteiner mounted volume> -z zoo1:2181

## Issues
Whenever restart container, need to remove and create zookeeper volume. 
  - docker volume rm solrcloud_zoo1
  - docker volume create solrcloud_zoo1

## Follow this thread
https://issues.apache.org/jira/browse/SOLR-16131?jql=text%20~%20"Error%20loading%20class%20%27solr.SQLHandler%27"

