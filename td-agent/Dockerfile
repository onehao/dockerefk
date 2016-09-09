
FROM keto/td-agent

USER root
WORKDIR .
ADD td-agent.conf /etc/td-agent/td-agent.conf

RUN /usr/sbin/td-agent-gem install fluent-plugin-elasticsearch 

VOLUME ["/etc/td-agent"]

ENTRYPOINT ["td-agent"]
