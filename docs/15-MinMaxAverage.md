- Endpoint GET /basket
- Create a dashboard to show the amount of times a basket has been retrieved
- Extend the dashboard to show the min, average and max duration of the basket call
- Extend the dashboard to show the amount of failed calls (http 500) (fouten injecteren random?)
- Reboot, see reboot line?

# Min, Max, Average

Assuming you've just created a dashboard for the `get_basket_v1_seconds_count` metric we now have a dashboard that can tell us how many requests per seconds the endpoint is receiving. Quite an interesting metric, but it is not giving us the full picture yet. When handling a HTTP request we want it to be handled as fast as possible, in order to ensure a pleasant user experience. In the next steps we will add functions to show us the fastest (min), slowest(max) and average (avg) response times for the requests handled in that time period.