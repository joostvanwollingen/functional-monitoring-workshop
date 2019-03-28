# Introduction

These pages serve as documentation for the Functional Monitoring Workshop. You can work through the exercises at your own pace.

## System under test
The system under test is a simple backend for a shopping basket, called TRIX. You can find the documentation of the API on: [**insert url**](http://some.url). It has operations to create a new basket, add items to a basket, retrieve payment providers and order the items. We do assume you are familiar with [HTTP REST](https://spring.io/understanding/REST).

## Tools
### Grafana
In the first exercises we will set up a basic dashboard in [**Grafana**](url_to_grafana) which we can use to monitor the system. See if you can reach the url above, as you will need Grafana for every exercise.

### Prometheus
The metrics visualized by Grafana are coming from [Prometheus](https://prometheus.io/). Prometheus gathers those metrics from the services and applications to be monitored. The Prometheus [documentation](https://prometheus.io/docs/introduction/overview/) describes the [PromQL query language](https://prometheus.io/docs/prometheus/latest/querying/basics/) which is what we will be using during this workshop.

### Postman
To do requests to the system under test [Postman](https://www.getpostman.com/downloads/) is a nice, visual REST client that is easy to use. Please install Postman and get the [**request collection**](collection_url).

# Ready?
Once you are ready move on to the first exercise in the sidebar on the left.