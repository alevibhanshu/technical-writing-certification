# Food Ordering API Documentation

## 1. Overview
The Food Ordering API allows developers to interact with the platform to manage users, restaurants, and orders.

Base URL: https://api.foodapp.com/v1

Content-Type: application/json


---

## 2. Authentication

### Endpoint
POST /auth/login


### Description
Authenticates a user and returns an access token.


### Request Body

{
  "email": "user@example.com",
  "password": "password123"
}

### **Response**

{
  "token": "abc123xyz",
  "expires_in": 3600
}

## 3. Get All Restaurants

### Endpoint

GET /restaurants

### Description

Fetches a list of available restaurants.

### Headers

Authorization: Bearer <token>

### Response

[
  {
    "id": 1,
    "name": "Spicy Hub",
    "rating": 4.5
  },
  {
    "id": 2,
    "name": "Food Palace",
    "rating": 4.2
  }
]

## 4. Get Restaurant Menu

### Endpoint

GET /restaurants/{id}/menu

### Description

Retrieves menu items for a specific restaurant.

### Path Parameter

| Parameter | Type    | Description   |
| --------- | ------- | ------------- |
| id        | integer | Restaurant ID |


### Response

[
  {
    "item_id": 101,
    "name": "Veg Burger",
    "price": 120
  },
  {
    "item_id": 102,
    "name": "Pizza",
    "price": 250
  }
]

## 5. Create Order

### Endpoint
POST /orders

### Description

Places a new order.

### Headers

Authorization: Bearer <token>

### Request Body

{
  "restaurant_id": 1,
  "items": [
    {
      "item_id": 101,
      "quantity": 2
    }
  ],
  "payment_method": "UPI"
}

### Response
{
  "order_id": 5001,
  "status": "confirmed",
  "estimated_delivery_time": "30 mins"
}

## 6. Track Order

### Endpoint

GET /orders/{order_id}

### Description

Fetches order status.

### Response

{
  "order_id": 5001,
  "status": "out_for_delivery"
}

## 7. Error Handling

| Status Code | Description  |
| ----------- | ------------ |
| 400         | Bad Request  |
| 401         | Unauthorized |
| 404         | Not Found    |
| 500         | Server Error |

## 8. Conclusion

This API enables developers to integrate food ordering features such as browsing restaurants, placing orders, and tracking deliveries.
