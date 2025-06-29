---
description: API documentation for /petdex
icon: shield-cat
---

# Petdex

## Get all pet species

<mark style="color:green;">`GET`</mark> `/petdex`

Gets all the pet types that are possible

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
        "name": "XSS Webspinner",
        "type1": 1
    },
    {
        "id": 2,
        "name": "SQL Serpent",
        "type1": 2
    },
    {
        "id": 3,
        "name": "CSRF Corgi",
        "type1": 3
    },
    {
        "id": 4,
        "name": "Redirect Rabbit",
        "type1": 4
    },
    {
        "id": 5,
        "name": "Deserialization Duck",
        "type1": 5
    },
    {
        "id": 6,
        "name": "Sensitive Seahorse",
        "type1": 6
    }
]
```
{% endtab %}
{% endtabs %}

## Read petdex by id

<mark style="color:green;">`GET`</mark> `/petdex/{id}`

Retrieve details of a specific petdex entry by providing their id .

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**params**

| Name | Type   | Description        |
| ---- | ------ | ------------------ |
| `id` | number | id of the pet type |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "id": 1,
    "name": "XSS Webspinner",
    "type1": 1
}
```
{% endtab %}

{% tab title="404" %}
```json
{
    "message": "Pet type not found"
}
```
{% endtab %}
{% endtabs %}

## Create a new petdex entry

<mark style="color:green;">`POST`</mark> `/petdex`

Creates a new pet type and responds with its inserted object.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name               | Type   | Description                       |
| ------------------ | ------ | --------------------------------- |
| `name`             | string | Name of the pet type              |
| `vulnerability_id` | number | Id of the vulnerability it boosts |

**Response**

{% tabs %}
{% tab title="201" %}
```json
{
    "id": 17,
    "name": "Reverse shell turtle",
    "type1": 2
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "message": "Error: vulnerability_id is undefined"
}
```
{% endtab %}

{% tab title="404" %}
```json
{
    "message": "Vuln not found"
}
```
{% endtab %}

{% tab title="409" %}
```json
{
    "message": "Petdex already exists"
}
```
{% endtab %}
{% endtabs %}
