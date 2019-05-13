# Working with queues

Situation: If you post to /orders to create an order the TRIX service will put a message on the 'new order queue'. Another process will verify the order and put a message on the 'confirmed order queue' that the TRIX service processes.

- Call endpoint to stop the processing of queued messages (new order queue & confirmed order queue)
- Create 500 new orders
- Adjust your dashboard to show the amount of messages on both queues (gauge)