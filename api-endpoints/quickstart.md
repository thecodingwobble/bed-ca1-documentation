---
description: Documentation for the /users endpoint
icon: user
---

# Users

## Register a new user

<mark style="color:green;">`POST`</mark> `/register`

Registers a new user. Returns a JWT token.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name       | Type   | Description          |
| ---------- | ------ | -------------------- |
| `username` | string | Name of the user     |
| `password` | string | Password of the user |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
   "message": 'User test created successfully.', 
   "token": '<TOKEN HERE>'
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  message: "Error: username or password is missing"
}
```
{% endtab %}

{% tab title="409" %}
```json
{
  message: "User already exists"
}
```
{% endtab %}
{% endtabs %}

## Log in

<mark style="color:green;">`POST`</mark> `/login`

Logs a user in. Returns a JWT token.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name       | Type   | Description          |
| ---------- | ------ | -------------------- |
| `username` | string | Name of the user     |
| `password` | string | Password of the user |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
   "token": '<TOKEN HERE>'
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  message: "Error: username or password is missing"
}
```
{% endtab %}
{% endtabs %}

## Get all users

<mark style="color:green;">`GET`</mark> `/leaderboard`

Retrieve a list of all users with their respective id, username, and reputation, etc sorted in order of total reputation. Used on frontend for users.html.

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
    "id": 3,
    "username": "turnWhiteHat",
    "reputation": 740,
    "points": 2620,
    "total_rep": 5740,
    "name": "Skilled Hunter"
  },
  {
    "id": 1,
    "username": "pentester123",
    "reputation": 1000,
    "points": 1000,
    "total_rep": 3500,
    "name": "Hunter"
  }
]
```
{% endtab %}
{% endtabs %}

## Read user by id

<mark style="color:green;">`GET`</mark> `/{id}/profile`

<mark style="color:green;">`GET`</mark> `/profile` <mark style="color:blue;">`JWT`</mark>

Retrieve details of a specific user by providing their id. used for singleUserInfo.html.

The endpoint /profile handles the currently authenticated user for the /profile endpoint.

**Headers**

| Name                     | Value              |
| ------------------------ | ------------------ |
| Content-Type             | `application/json` |
| Authorization (optional) | JWT bearer token   |

**params**

| Name | Type   | Description    |
| ---- | ------ | -------------- |
| `id` | number | id of the user |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "id": 1,
  "name": "pentester123",
  "reputation": 0
}
```
{% endtab %}

{% tab title="404" %}
```json
{
  "message": "User not found"
}
```
{% endtab %}
{% endtabs %}

## Update a user <mark style="color:$danger;background-color:$danger;">DEPRECIATED</mark>&#x20;

{% hint style="danger" %}
#### DEPRECIATED

This endpoint is depreciated, and WILL NOT work anymore for CA2.&#x20;
{% endhint %}

<mark style="color:green;">`PUT`</mark> `/users/{id}`

Update user details by providing id in the URL and updating user in the request body

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name         | Type   | Description            |
| ------------ | ------ | ---------------------- |
| `username`   | string | Name of the user       |
| `reputation` | number | reputation of the user |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "id": 1,
  "username": "turnWhiteHat",
  "reputation": 100
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "message": "Error: username or reputation is undefined"
}
```
{% endtab %}

{% tab title="404" %}
```json
{
  "message": "User not found"
}
```
{% endtab %}

{% tab title="409" %}


```json
{
  "message": "User already exists"
}
```
{% endtab %}
{% endtabs %}

## Get the next rank of the user <mark style="color:$danger;background-color:$danger;">DEPRECIATED</mark>&#x20;

{% hint style="danger" %}
#### DEPRECIATED

This endpoint is depreciated, and WILL NOT work anymore for CA2.&#x20;
{% endhint %}

<mark style="color:green;">`POST`</mark> `/users/{id}/next_rank`

Gets the next rank of the user

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name | Type   | Description    |
| ---- | ------ | -------------- |
| `id` | number | id of the user |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "id": 5,
    "name": "Skilled Hunter",
    "description": "The pinnacle of bug hunting, possessing unparalleled expertise and access to all elite abilities.",
    "threshold": 5000
}
```
{% endtab %}

{% tab title="404" %}
```json
{
    "message": "Rank not found"
}
```
{% endtab %}
{% endtabs %}

## Get user pets <mark style="color:$danger;background-color:$danger;">DEPRECIATED</mark>&#x20;

{% hint style="danger" %}
#### DEPRECIATED

This endpoint is depreciated, and WILL NOT work anymore for CA2.&#x20;
{% endhint %}

<mark style="color:green;">`POST`</mark> `/users/{id}/pets`

Gets all the pets a player owns.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name | Type   | Description    |
| ---- | ------ | -------------- |
| `id` | number | id of the user |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "id": 1,
        "dex_num": 6,
        "rarity_id": 1,
        "multiplier": 1,
        "type1": 6,
        "experience": 0
    },
    {
        "id": 3,
        "dex_num": 4,
        "rarity_id": 1,
        "multiplier": 1,
        "type1": 4,
        "experience": 0
    }
]
```
{% endtab %}

{% tab title="404" %}
```json
{
    "message": "User not found"
}
```
{% endtab %}
{% endtabs %}
