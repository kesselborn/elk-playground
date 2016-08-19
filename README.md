
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

