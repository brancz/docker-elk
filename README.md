Docker Logging Setup
====================

The ELK-Stack (ElasticSearch, Logstash, Kibana) is actually very known for
logging, but when I searched for a ready to use solution nothing statisfied me
to my need.

This logging setup that can be used to capture, store and visualize logs from
any source (see how to use with [Docker below](#capture-docker-logs)) that is
supported by logstash with for example a `key=value` format

	log_type=HTTP_LOG route=/my/route response_code=200

> Hint: This is the behaviour by my configuration, but can be adapted to your
> needs.

Simply start using it with:

	docker-compose up

> Hint: this `docker-compose.yml` also works perfectly on
> [rancher](rancher.com) :wink:

TODO
----

Authentication for accessing Kibana as well as pushing logs into Logstash!

Capture Docker Logs
-------------------

Using the docker logging driver to make docker send the plaintext logs to
the logstash instance using the syslog protocol.

	docker run --log-driver=syslog --log-opt syslog-address=udp://elk-hostname:5140 myimage
