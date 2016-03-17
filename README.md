#fluentd-to-splunk

This creates a docker container that can read kubernetes logs and pass them on to splunk. This image is based on https://github.com/kubernetes/kubernetes/blob/master/cluster/addons/fluentd-elasticsearch/fluentd-es-image/Dockerfile

# build

You must have docker-machine running.


 ```mvn clean install```

This is will create the docker image: paulkane/fluentd-to-splunk:1.1-SNAPSHOT


# Splunk kubernetes yaml

Place ```fluentd-splunk.yaml``` on your minions. This is a Pod.

```splunk-forward-rc.yaml``` and ```splunk-forward-svc.yaml``` takes the output from fluentd and forwards them to the splunk server defined by ```SPLUNK_FORWARD_SERVER```
```splunk-rc.yaml``` and ```splunk-svc.yaml``` is the admin UI where you can view the splunk logs.

splunk admin: http://127.0.0.1:30010/

## Receive data

Settings --> data --> receiving:  set the port to 9997

```
inputs.conf
[splunktcp://9997]
disabled = 0
```

## forwarder

You might want to set allow remote login to always

```
server.conf
[general]
allowRemoteLogin=always
```


# docker splunk
 docker splunk images provided by outcoldman

 How to use the docker splunk: https://github.com/outcoldman/docker-splunk

