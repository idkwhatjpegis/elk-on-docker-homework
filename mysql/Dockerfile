FROM mysql

# Initially taken from https://github.com/aboullaite/docker-elk

ENV DEBIAN_FRONTEND noninteractive

### install MetricBeat

ENV METRICBEAT_VERSION 8.4.3

RUN apt-get update -qq \
 && apt-get install -qqy curl \
 && apt-get clean

RUN curl -L -O https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-${METRICBEAT_VERSION}-amd64.deb \
 && dpkg -i metricbeat-${METRICBEAT_VERSION}-amd64.deb \
 && rm metricbeat-${METRICBEAT_VERSION}-amd64.deb


###############################################################################
#                                CONFIGURATION
###############################################################################

### tweak nginx image set-up

### configure MetricBeat

# config file
ADD metricbeat.yml /etc/metricbeat/metricbeat.yml
RUN chmod go-w /etc/metricbeat/metricbeat.yml

###############################################################################
#                                    DATA
###############################################################################

###############################################################################
#                                    START
###############################################################################

ADD ./start.sh /usr/local/bin/start.sh
RUN chmod +x /usr/local/bin/start.sh
CMD [ "/usr/local/bin/start.sh" ]
