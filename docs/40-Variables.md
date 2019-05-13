# Using variable to split out per environment

You don't want to create a new dashboard for every environment, but you want to reuse the same dashboard for all environments you work on. That is why Grafana supports [dashboard Templating](https://grafana.com/docs/v3.1/reference/templating/). This allows you to make your Dashboards more interactive and dynamic.

Grafana also provides some Official & community built dashboards which you can download on: https://grafana.com/dashboards We have already downloaded dashboard 'JVM (Micrometer)' in Grafana. Look around on this dashboard and play with the variables on the top. Now try to make this more readable and easier to use. 

Create a new variable 'environment-yourteamnumber' and with the use of regular-expressions extract the 'app-environment' names: trix-pro and trix-staging.


<details><summary>Need help?</summary>
<p>Query of the instance to be used in the Grafan Query Options: label_values(jvm_memory_used_bytes{application="$application"}, instance)</p>
<p>Regex tip: /^(.*environmentName|.*environmentName)/"</p>
</details>

<details><summary>I can't take it anymore, just give me the solution.</summary>
<img src="images/templating.png" />
</details>
