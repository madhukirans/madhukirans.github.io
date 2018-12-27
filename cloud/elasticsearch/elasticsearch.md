##ElasticSearch [ES]
###Node types
* Master
  * Master node controls cluster
  * Node become master by setting "node.master: true" in elasticsearch.yaml
* Data
  * Data nodes stores the data. Basically user does CRUD operations.
  * Basically user inserts and searches through data nodes  
  * Node become data by setting "node.data: true" in elasticsearch.yaml
* Ingest
  * If the desire is to transform data before insert then ingest nodes are used
  * Node become ingest by setting "node.ingest: true" in elasticsearch.yaml
* Client
  * These nodes handles search requests.
  * They active as smart load balancers
  * Node become client by setting "node.master: false", "node.data: false", "node.ingest: false" in elasticsearch.yaml
* Tribe
  * Provide search operations across multiple clusters.