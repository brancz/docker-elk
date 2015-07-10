Docker Logging Setup
====================

A Docker logging setup that can be used to capture, store and visualize logs
from any Docker log that is in the format of a key-value list like

	log_type=HTTP_LOG route=/my/route response_code=200

> Hint: This is the default behaviour, by my configuration but can be adapted
> to your needs.

Simply start using it with:

	docker-compose up

> Hint: this can also be used on Docker platforms such as tutum. To capture
> logs from all your docker hosts, make sure you deploy the `logspout`
> container to all hosts. (refer to the services documentation to find the
> corresponding option)

Software Stack:

* ElasticSearch
* Logstash
* Kibana
* Logspout

TODO
----

Authentication for accessing Kibana as well as pushing logs into Logstash!

How it works
------------

The ELK-Stack (ElasticSearch, Logstash, Kibana) is actually very known for
logging, but when I searched for a ready to use solution nothing statisfied me
to my need.

Logspout takes the pure Docker log output and sends it via UDP to Logstash.
Logstash then parses the log line by line. (By my configuration the log is
expected to be key-value) After parsing the log line the key-value pairs are
stored in ElasticSearch. The ElasticSearch index can then be visualized and
analyzed with Kibana.
