---
description: API documentation for /vulnerabilities
icon: laptop-code
---

# Vulnerabilties

## Get all vulnerabilities

<mark style="color:green;">`GET`</mark> `/vulnerabilities`

Retrieve a list of all vulnerabilities.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
  {
    "id": 1,
    "type": "SQL Injection",
    "description": "The login form is vulnerable to SQL Injection.",
    "points": 100
  },
  {
    "id": 2,
    "type": "Cross-Site Scripting",
    "description": "The homepage is vulnerable to reflected XSS.",
    "points": 50
  }
]
```
{% endtab %}
{% endtabs %}

***

## Create a new vulnerability class <mark style="color:$danger;background-color:$danger;">DEPRECIATED</mark>&#x20;

{% hint style="danger" %}
#### DEPRECIATED

This endpoint is depreciated, and WILL NOT work anymore for CA2.&#x20;
{% endhint %}

<mark style="color:orange;">`POST`</mark> `/vulnerabilities`

Create a new vulnerability by providing type, description, and points in the request\
body. Upon successful creation, the id of the newly generated id will be returned.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name          | Type   | Description                                        |
| ------------- | ------ | -------------------------------------------------- |
| `type`        | string | Type of vulnerability                              |
| `description` | string | Description of the vulnerability                   |
| `points`      | number | Number of points associated with the vulnerability |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "id": 1
}
```

| Name | Type | Description                           |
| ---- | ---- | ------------------------------------- |
| id   | int  | id of the newly created vulnerability |
{% endtab %}

{% tab title="400" %}
```json
{ 
  message: "Error: type, description or points is missing" 
}
```
{% endtab %}
{% endtabs %}

###

