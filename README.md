
# elk playground

A `docker-compose.yml` file + logstash configs that set start an ELK stack and ingest the docker logs in a structured form (see logstash config), so you can play around with Kibana.

# how to
run

    docker-compose up

once you see logstash messages scrolling by, point your browser to [http://localhost:5601](http://localhost:5601) (or the docker host that you usually have to use), click `create` and browse to the `Discover` tab.

You will already see indexed messages.

In order to get messages with the `@level=error`, do a docker pull of a non existant image:

    docker pull asdgasdgsadfa

the error message should show up in the index after reload as we ingest all docker log messages.

# moar data

If you want more data you can instruct logstash to not only ingest new logs but also all previous docker logs. In order to activate this, edit `logstash/conf.d/input.conf` (see comments there), stop the elk cluster if you already started it (`docker-compose stop && docker-compose rm` (the `rm` is important)) and start the elk cluster again. This will spin up your CPU ;)
