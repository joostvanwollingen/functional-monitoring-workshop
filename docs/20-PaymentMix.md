# Visualize how orders are payed for

## About the /orders endpoint
In this exercise we will use a different endpoint, namely the POST /orders endpoint. 
This endpoint is used whenever a customer places a new order. The request body looks like the example below.

```
{
  "customerId": "string",
  "orderNumber": "string",
  "orderPriceCents": 0,
  "paymentMethod": "string",
  "totalItemCount": 0
}```

Whenever the paymentMethod has a value of `iDeal`, `CreditCard` or `PostPaid` its corresponding metric is increased: `createOrderPaymentMethod_creditcardv1_total`, `createOrderPaymentMethod_idealv1_total` or `createOrderPaymentMethod_postpaidv1_total`. 

The Postman collection contains a request for this endpoint, which will randomly use one of the three paymentMethods whenever the request is executed.

## Dashboard

Create a dashboard that shows the total amount of orders placed, the amount of orders per payment type and uses the $__range function to only show the orders placed in the selected time window.

![Your dashboard should look something like this](images/exercise3.png ':size=700')
