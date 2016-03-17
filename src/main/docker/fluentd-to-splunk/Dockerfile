# Adapted from
# https://github.com/kubernetes/kubernetes/blob/master/cluster/addons/fluentd-elasticsearch/fluentd-es-image/Dockerfile

FROM gcr.io/google_containers/fluentd-elasticsearch:1.12

RUN td-agent-gem install fluent-plugin-splunkapi

# Copy the Fluentd configuration file.
COPY td-agent.conf /etc/td-agent/td-agent.conf

# Run the Fluentd service.
ENTRYPOINT ["td-agent"]