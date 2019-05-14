# Setup Alerts

Following on the previous exercise we want to generate an [alert](https://grafana.com/docs/alerting/rules/) and send a notification to a Slack channel when the 3rd party service becomes slow again.

We've already set up an integration between Grafana and Slack, which allows Grafana to sent notifcations whenever a certain condition is met. Ask the workshop organizers to show the Slack channel on the beamer if they aren't already!

Adjust your panel from the previous exercise to send and alert whenever the 3rd party is too slow. 

![Your dashboard should look something like this](images/alerts.png ':size=700')