FROM kibana:4.6.0

RUN apt-get update && apt-get install -y netcat

COPY entrypoint.sh /tmp/entrypoint.sh
RUN chmod +x /tmp/entrypoint.sh

COPY config/kibana.yml /opt/kibana/config/kibana.yml

RUN kibana plugin --install elastic/sense
RUN kibana plugin --install elasticsearch/marvel/latest

CMD ["/tmp/entrypoint.sh"]
