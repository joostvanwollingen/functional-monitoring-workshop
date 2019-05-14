# Introduction

These pages serve as documentation for the Functional Monitoring Workshop. You can work through the exercises at your own pace.

## System under test
The system under test is a simple backend service, called TRIX. You can find the documentation of the API in [Swagger](https://trix-pro.cfapps.io/swagger-ui.html#/). It has different operations to create a new customer, add and delete them, but also operations to create orders, add items to an order and retrieve them. A completely fictional API. We do assume you are familiar with [HTTP REST](https://spring.io/understanding/REST).

Every group (or individual) gets a number and does the exercises against a separate instance of the Trix service so it is easier to see your own requests.

Trix example URL per group:

|Group|Trix URL|
| ------------- |:-------------:|
|1| https://trix-1-dev.cfapps.io/swagger-ui.html|
|2| https://trix-2-dev.cfapps.io/swagger-ui.html|
|3| https://trix-3-dev.cfapps.io/swagger-ui.html|
|...| ...|
|10| https://trix-10-dev.cfapps.io/swagger-ui.html|

## Tools
### Grafana
In the exercises we will set up dashboards in [**Grafana**](https://idb-grafana-616.cfapps.io/) which we can use to monitor the system. See if you can reach the url above, as you will need Grafana for every exercise. If needed login with password and username: admin/admin.

### Prometheus
The metrics visualized by Grafana are coming from [Prometheus](https://prometheus.io/). Prometheus gathers those metrics from the services and applications to be monitored. The Prometheus [documentation](https://prometheus.io/docs/introduction/overview/) describes the [PromQL query language](https://prometheus.io/docs/prometheus/latest/querying/basics/) which is what we will be using during this workshop to query the right data for our visualizations.

### Postman
To do requests to the system under test [Postman](https://www.getpostman.com/downloads/) is a nice, visual REST client that is easy to use. Please install Postman and get the [**request collection**](https://www.getpostman.com/collections/53dd09921ee3f3b290f0).

### WRK
[WRK](https://github.com/wg/wrk) is a HTTP benchmarking tool, which can be used to fire thousands of requests in a short amount of time at the SUT. That way we can generate more realistic metrics to create dashboards with.

#### Generate requests with WRK

In order to use WRK you need to either install it [locally](https://github.com/wg/wrk/wiki/Installing-wrk-on-Windows-10) or use [Docker](https://github.com/William-Yeh/docker-wrk). 

Before you execute the following commands change the URL for your version of Trix.

Example URL: ```https://trix-pro.cfapps.io``` 

Locally:
```wrk -t1 -d10 https://trix-pro.cfapps.io/customers```

Docker:
```docker run --rm williamyeh/wrk -t1 -d10 https://trix-pro.cfapps.io/customers```

In case you are developing and run Trix locally.

Locally:
```wrk -t1 -d10 http://{hostname}:9999/customers```

Docker:
```docker run --rm williamyeh/wrk -t1 -d10 http://{hostname}:9999/customers```

# Ready?
Once you are ready move on to the first exercise in the sidebar on the left.