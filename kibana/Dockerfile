FROM docker.elastic.co/kibana/kibana:6.1.3

USER root

COPY ./config/kibana.yml /usr/share/kibana/config/kibana.yml

COPY config/wait-for-it.sh /wait-for-it.sh

ADD https://packages.wazuh.com/wazuhapp/wazuhapp-3.1.0_6.1.3.zip /tmp

ADD https://raw.githubusercontent.com/wazuh/wazuh/3.1/extensions/elasticsearch/wazuh-elastic6-template-alerts.json /usr/share/kibana/config

ADD https://raw.githubusercontent.com/wazuh/wazuh/3.1/extensions/elasticsearch/wazuh-elastic6-template-monitoring.json /usr/share/kibana/config

ADD https://raw.githubusercontent.com/wazuh/wazuh/3.1/extensions/elasticsearch/alert_sample.json /usr/share/kibana/config

RUN /usr/share/kibana/bin/kibana-plugin install file:///tmp/wazuhapp-3.1.0_6.1.3.zip

RUN rm -rf /tmp/*

RUN chmod 755 /wait-for-it.sh
