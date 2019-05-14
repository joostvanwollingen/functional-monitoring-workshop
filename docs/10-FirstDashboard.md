# Your first dashboard

Let's start by creating a dashboard on which we can see the details of the GET /customers endpoint. 

## Start with downloading a template dashboard
Because we all work on one shared instance of Grafana it is important to start with a template dashboard where you can select the instance of Trix you are testing on. 

Find the template dashboard in [Grafana](https://idb-grafana-616.cfapps.io/). Go to the settings of the template dashboard. On the left hand side click `Save as` and give your dashboard a unique name. 

What the template dashboard does is create a variable for you called `$instance`. Its value is determined by the dropdown at the top of the dashboard. This way we can easily add a filter to each query, by adding a [label](https://prometheus.io/docs/prometheus/latest/querying/basics/#time-series-selectors) filter. How to use those is explained below.

You can do all exercises on this copy of the template dashboard. Keep in mind there is no user authentication on deleting or altering dashboards from other teams during this workshop.

## Add a panel
![Click the Add Panel button](images/add_panel.png ':size=150')

On the new dashboard click the `Add Panel` button. Then click `Add Query`. Each panel can consist of multiple queries which will be shown in the visualization type you've chosen.

Type `get_` in the first query field `A`. The autocomplete function will show you all the available metrics that start with whatever your input is. Choose `get_customers_v1_seconds_count` for now, this is the metric that shows us the number of requests to the GET Customers endpoint per second.

## Filtering for our own instance
Depending on how many instances of the Trix service there are you may get a lot of different times series for this query. It is now retrieving all requests for all instances of the service on the GET customers endpoint. Let's limit this to only the instance that you or your team are working on by adding a [label](https://prometheus.io/docs/prometheus/latest/querying/basics/#time-series-selectors) filter. The label name to use in your query is `instance` and the value is determined by the instance dropdown at the top of the dashboard. To refer to that value you can use `$instance`. The final query would be: `get_customers_v1_seconds_count{instance="$instance"}`.

![Make sure to select the right instance](images/dropdown_instance_filter.png ':size=700')

## Generate some metrics
The current graph is probably empty, because we don't have any metrics yet. Change the time range in the top right hand corner to show the metrics for the last 5 minutes. Now use the Postman request 'GET Customers' to generate some data points. Refresh the dashboard page with the icon in the top right hand corner. This time you should see the graph being drawn.
## Not quite what you expected?
As time passes you'll notice that the graph stays at the same level, even though no new requests are coming in. This is because of [how counters work in Promotheus](https://www.robustperception.io/how-does-a-prometheus-counter-work). In order to see the real amount of requests per seconds we will need to adjust the query in Grafana to account for this. 

We can use a function to take the data from the time series and convert it into a value that better reflects what was happening at that moment in time. 

Experiment with the [`irate`](https://prometheus.io/docs/prometheus/latest/querying/functions/#irate) and [`increase`](https://prometheus.io/docs/prometheus/latest/querying/functions/#increase) functions. What are the differences between the two?

<details><summary>Need help with the irate and increase functions?</summary>
<p>

```
While editing the panel click the `Add query` button on the right, it will add an additional input field `B`
Query A: irate(get_customers_v1_seconds_count{status="200", instance="$instance"}[1m])
Query B: increase(get_customers_v1_seconds_count{status="200", instance="$instance"}[1m])
Enter a descriptive name in the respective legend fields. 
Clicking on the small colored line in front of the series, just below the graph, allow you to choose a color for the series.
```
<img src="images/rate_increase.png" width=500px><br/>
</p>
</details>

## Labels

You might see two series drawn per query, this is because there are [labels](https://prometheus.io/docs/prometheus/latest/querying/basics/#time-series-selectors) in the time series. To only focus on the successful requests for example, you could add `{status="200"}`. You can combine labels with a `,`, i.e. `{status="200", instance="$instance"}`.

## Before moving on

Experiment a little with the available styling options for your graph and setting a unit for the Y-axis before you move on to the second exercise.

![Your dashboard should look something like this](images/exercise1.png ':size=700')
