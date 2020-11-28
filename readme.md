# Prometheus Jenkins

The purpose of this repo is to provide a Dockerfile to support Prometheus and its use to extract metrics from a Jenkins server

## Installation

Clone the repository, cd into it and run docker build -t my-prometheus .  
the space and period are important in the above command.
To get Prometheus up and running in a Docker container run the command  
docker run -d -p 9090:9090 my-prometheus  
if you visit localhost:9090 you'll be greeted by the Prometheus dashboard.  
![](images/prometheus.png?raw=true)

## Use cases
As you may have gathered by the yml file the specific use case laid out here is for using the Prometheus plugin for Jenkins CI/CD pipeline to expose metrics that can be graphed in Prometheus or even to Grafana.
Links for plugin and more here:  
[plugin](https://plugins.jenkins.io/prometheus/)  
Other useful links here:  
[Grafana](https://grafana.com/)  
[Dockerized Grafana](https://hub.docker.com/r/grafana/grafana/)  
[Mixing it all together](https://medium.com/@eng.mohamed.m.saeed/monitoring-jenkins-with-grafana-and-prometheus-a7e037cbb376)
## Cool additions  
There are a few things not touched on in the article, on of which is when configuring a dockerized version of Prometheus to a dockerized version of Grafana you'll need the containers url for connection Prometheus as a data source  
```bash
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' xxxxxxxxx id of container
```  
The bash command will yield the ip address of the docker container Prometheus is running on.  
If you decide to run Grafana and honestly why wouldn't you? Grafana has a pretty deep library of prebuilt plugins itself this one: [Grafana plugin](https://grafana.com/grafana/dashboards/9524) is pretty amazing, have a look.
## Before I go, whats Jenkins?  
Jenkins is a robust ci/cd framework written in Java and scripted in Groovy.  
It is used to pull code, check, build, test, deploy and produce artifacts.  
I'll provide some helpful links for Installing and also running it on Docker.  

[Jenkins](https://www.jenkins.io/doc/book/installing/)  
[Dockerized Jenkins](https://hub.docker.com/r/jenkins/jenkins)  
## Finally  
This hopefully provides some good material to make a pretty robust system of not only running a ci/cd pipeline but also having a container available that monitors and provides a very useful graph to inform you of status and health
