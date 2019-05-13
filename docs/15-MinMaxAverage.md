# Min, Max, Average

Assuming you've just created a dashboard for the `get_customer_v1_seconds_count` metric we now have a dashboard that can tell us how many requests per seconds the endpoint is receiving. Quite an interesting metric, but it is not giving us the full picture yet. When handling a HTTP request we want it to be handled as fast as possible, in order to ensure a pleasant user experience. Create a graph to show us the fastest (min), slowest(max) and average (avg) response times for the requests handled in that time period. For that you can use the [aggregation operators](https://prometheus.io/docs/prometheus/latest/querying/operators/#aggregation-operators): `min`, `max`, `avg`.

In this case its easier to use WRK to generate a large number of requests instead of Postman. Use wrk with 2 threads for 30 seconds to generate requests. If you want to figure out how to use WRK, simply run `wrk` on the command-line. 

## Number of calls
Using the single stat pane it is easy to show a single number, for example with the amount of calls recieved by the endpoint in the first place. Figure out how to show the total amount of calls placed ever and the total amount of calls placed in the last selected time range. For that you can use a special time range vector variable called [`$__range`](https://grafana.com/docs/features/datasources/prometheus/#using-interval-and-range-variables) in combination with the [`increase`](https://prometheus.io/docs/prometheus/latest/querying/functions/#increase) function we've used before..

## Failures?
Finally we'll also want to show how many calls failed with an `ApplicationException`. Use [`labels`](https://prometheus.io/docs/prometheus/latest/querying/basics/#time-series-selectors) to fine tune your query and only show the failed calls in a single stat pane.

To better show the balance between failed and passed calls see if you can combine the two queries in a single bar graph.



![Your dashboard should look something like this](images/exercise2.png ':size=700')
