# ElasticSearch, Logstash and Kibana
The ELK Stack is the combination of Elasticsearch, Logstash, and Kibana that is used specifically in log analytics. Logstash ships log data to Elasticsearch, which indexes the information in a searchable datastore. Kibana then takes the datastore and shows the information in graphical format for log analysis.
Logstash is developed by Ruby,  Kibana by javascript, Elasticsearch by Java

## ELK setting in CentOS
We can use script to install ELK in CentOS

## Questions for Scala and AKKA
Q1:  How to use the scalability of AKKA? what’s you use environment?  
Benefit for Scala  develop Backend APIs  
Speed,, no overhead, less CPU,  Less code, Scaliabity  
AKKA.io  package : event -driven , non-blocking, async  
Play!  
Lift  

Q2:  What’s the advantage and disadvantage of AKKA and Scala to develop the RESTful APIs?  

##Kafka
(1)  Web activty tracking:  web page , user operation, send to Kafka
(2)  Log aggregation :  Monitor and offline analyze log
   Producer:   application  send operation log  synchronize  to Kafka cluster
  Consumer:  user hadoop + elastic search  to
(3) You mentioned  Erlang,.l  only use the payment component by Erlang

