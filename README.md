# Well Architected Review - Elasticsearch
Based-on AWS Well-Architected Review, this content is used for Elasticsearch, especially Centralized-Logging or Monitoring use case.

## General Questions
* What is the purpose of system, scope of system?
* What is application related on this system?
* What is the impact when the system is outage?
* Is this system directly affect with revenue of business?
* What is current version of Elastic Stack?
* What is the infrastructure underlying of Elastic Stack?
    * (EC2/VM-based) What is JRE/JDK version?
* What is Elasticsearch licensing/distribution?
* Do you use any 3rd party plugins of Elastic Stack?

## Pliar 1: Security
* Where you deploy Elasticsearch (Public/Private of VPC Subnet)?
    * (If version less than 6.7) Are you aware about security inside Elasticsearch, especially OSS or Basic license?
* How do you manage authentication of Elasticsearch?
* How do you manage authorization of Elasticsearch?
* Have you used index-level authorization?
* Have you used field, document-level authorization?
* Have you enabled client encryption (HTTPS) for  Elasticsearch?
* Have you enabled node-to-node encryption for  Elasticsearch?
* Have you enabled encryption at rest for Elasticsearch?
    * (EC2/VM-based) How do you manage encryption keys?
* Have you enabled audit trail for Elasticsearch API?
    * (EC2/VM-based) Have you enabled audit trail for resource and configuration?

## Pliar 2: Reliability
* Have you separate Elasticsearch node type (Master, Data, Client, Ingest, Tribe, ML)?
    * (if yes) How many components for each type?
    * (EC2/VM-based) How do you failover of client endpoint?
        * (if yes) How you do health check for Load Balancer?
* How do you backup/snapshot Elasticsearch index?
    * (if yes) Where is the backup storage?
    * (if yes) How you guarantee HA for backup storage?
* How many replica shard that you configured for each index?
* Have you design replica shard as difference AZ?
* Have you controlled concurrent shard allocation?
* Have you controlled concurrent shard rebalancing?
* Have you setup index recovery speed?
* Have you controlled balancing of shard ?
* Have you enabled 'action.destructive_requires_name' at cluster setting?
* Are you using index alias for flexible mapping control?

## Pliar 3: Performance
* How many index shard per Elasticsearch instance?
* How much size per shard for Elasticsearch instance?
    * (if exceed) Do you know, rollover API can help you?
* Are you aware Ingest Node for Logstash replacement?
* Do you know, you can trade real-time for write performance?
* Are you using federated/cross cluster search?
* Do you know the differecne performance of 'text' and 'keyword' type?
* Have you used Fielddata Cache for aggregation?
* Are you aware about circuit breaker features?
* Have you enabled slow logs for Elasticsearch query?
* (EC2/VM-based) What is ratio of Heap and OS memory?
* (EC2/VM-based) What is System and Base check configuration of OS in Elasticsearch Instance?
* Are you using any painless script on Elasticsearch  cluster?
* Are you using Index Sorting for improve read performance?

## Pliar 4: Operational Excellance
* How do you monitor Elasticsearch metrics?
    * (EC2/VM-based) Have you monitored thread queue/rejection?
* How do you monitor Master Node metrics and JVM Heap usage?
* How do you monitor JVM and Heap metrics?
* How do you monitor OS metrics?
* How do you monitor other related components? (Beats, Logstash)
* How do you monitor Elastic stack logs? (ES, Kibana, Beats, Logstash)
* (EC2/VM-based) How do you archive old Elastic stack logs?
* How do you setup alert for monitored metrics?
* How do you provision stack components?
* How do you upgrade Elastics stack version?

## Pliar 5: Cost Optimization
* How do you manage index lifecycle? (Hot, Warm, Cold)
    * (if yes) Do you know, you can control index allocation by node?
    * (if yes) What is policy for hot-warm indices?
* Are you aware Amazon ES Ultra-warm feature for Hot-Warm strategy?
* How do you archive old time-series indices?
* Are you aware that Amazon ES can buy Reserved Instance?
* Do you know, you can reduce storage size by change mapping? For replacement automated 'text' and 'keyword' fields.
* Are you using rollup API for reduce storage size?