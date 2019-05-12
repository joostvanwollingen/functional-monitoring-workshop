# Your first dashboard

Let's start by creating a dashboard on which we can see the details of the GET /customers endpoint. 

In order to create a panel we will first need to create a dashboard in [Grafana](url). On the Grafana homepage click the + icon on the left hand side. If you don't see the + icon straight away you may have to click the Granafa logo in the topleft, that should unhide the toolbar. 

![Click the plus to create a new dashboard](images/create_new_dashboard.png ':size=250')
## Add a query
On the new dashboard click `Add Query`. This will add a panel for you. Each panel can consist of multiple queries which will be shown in the visualization type you've chosen.

Type `get_` in the first query field A. The autocomplete function will show you all the available metrics that start with whatever your input is. Choose `get_customers_v1_seconds_count` for now, this is the metric that shows us the number of requests to the GET Customers endpoint per second.
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
Query A: irate(get_customers_v1_seconds_count{status="200"}[1m])
Query B: increase(get_customers_v1_seconds_count{status="200"}[1m])
Enter a descriptive name in the respective legend fields. 
Clicking on the small colored line in front of the series, just below the graph, allow you to choose a color for the series.
```
<img src="images/rate_increase.png" width=500px><br/>
</p>
</details>

## Labels

You might see two series drawn per query, this is because there are [labels](https://prometheus.io/docs/prometheus/latest/querying/basics/#time-series-selectors) in the time series. To only focus on the successful requests for example, you could add `{status="200"}`.

## Before moving on

Experiment a little with the available styling options for your graph and setting a unit for the Y-axis before you move on to the second exercise.

![Your dashboard should look something like this](images/exercise1.png ':size=700')
