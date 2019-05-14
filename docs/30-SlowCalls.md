# Retrieving a customer by id is sometimes slow

Customers are complaining that when loading their profile the page sometimes takes a long time to load. The culprit has been identified and appears to be the GET `/customers/{id}` call. It retrieves all the details for a single customer.
Some of the details are retrieved from a 3rd party service. Its metrics are prefixed with `get_3rdPartyEnrichCustomerService_v3_seconds`. 

Figure out and visualize how much time the calls to the 3rd party service take and how it compares to the total duration of the call. Make sure to also use the metric `get_customerById_v1_seconds`.

Use WRK to generate the necessary load: `wrk -t1 -d180 http://{host}:{port}/customers/1`

<details><summary>Need help?</summary>
<p>The get_3rdPartyEnrichCustomerService_v3_seconds metric behaves slightly different. In order to get the average duration of calls to the 3rd party services you have to divide the <a target="_blank" href="https://prometheus.io/docs/practices/histograms/#count-and-sum-of-observations
">sum by the count of observations</a>.
</p>
</details>

![Your dashboard should look something like this](images/exercise4.png ':size=700')