---
description: Documentation for the /ranks endpoint
icon: turn-up
---

# Ranks

## Get all ranks

<mark style="color:green;">`GET`</mark> `/ranks`

Gets all the ranks in the database

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "id": 1,
        "name": "Novice",
        "description": "Initiate of the elite guild of bug hunters, beginning the journey with basic privileges.",
        "threshold": 0
    },
    {
        "id": 2,
        "name": "Tracker",
        "description": "Skilled in following subtle traces of bugs, refining investigative techniques and building a solid foundation for advanced tools.",
        "threshold": 500
    },
    {
        "id": 3,
        "name": "Junior Hunter",
        "description": "Demonstrates keen insight in vulnerability detection and methodical system analysis, unlocking more specialized equipment.",
        "threshold": 1000
    },
    ...,
]
```

| Name          | Type   | Description                              |
| ------------- | ------ | ---------------------------------------- |
| `id`          | number | id of the rank                           |
| `name`        | string | name of the rank                         |
| `description` | string | description of the rank                  |
| `threshold`   | number | Amount of reputation required to rank up |
{% endtab %}
{% endtabs %}

## Read rank by id

<mark style="color:green;">`GET`</mark> `/rank/{id}`

Retrieve details of a specific rank by providing their id .

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**params**

| Name | Type   | Description    |
| ---- | ------ | -------------- |
| `id` | number | id of the rank |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "id": 1,
    "name": "Novice",
    "description": "Initiate of the elite guild of bug hunters, beginning the journey with basic privileges.",
    "threshold": 0
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

## Update a rank

<mark style="color:green;">`PUT`</mark> `/rank/{id}`

Updates the rank based on the body provided. Rank to update is based on the id in the params. Returns the updated rank record as response.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name          | Type   | Description             |
| ------------- | ------ | ----------------------- |
| `name`        | string | Name of the Rank        |
| `description` | string | Description of the Rank |
| `threshold`   | number | Threshold of the Rank   |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "id": 7,
    "name": "Skilled Analyst",
    "description": "A skilled analyser, able to sniff out vulnerabilities from any application",
    "threshold": 15000
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "message": "Error: name or description or threshold is undefined"
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

## Create a new rank

<mark style="color:green;">`POST`</mark> `/rank`

Creates a new rank, and returns the newly created rank.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name          | Type   | Description             |
| ------------- | ------ | ----------------------- |
| `name`        | string | Name of the Rank        |
| `description` | string | Description of the Rank |
| `threshold`   | number | Threshold of the Rank   |

**Response**

{% tabs %}
{% tab title="201" %}
```json
{
    "id": 13,
    "name": "Ultra analyst",
    "description": "The ultra analyst, peak of the code analysts",
    "threshold": 15000
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "message": "Error: required fields is missing"
}
```
{% endtab %}

{% tab title="409" %}
```json
{
    "message": "Rank already exists"
}
```
{% endtab %}
{% endtabs %}
