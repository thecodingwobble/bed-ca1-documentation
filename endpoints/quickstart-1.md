---
description: Documentation for the /lootbox endpoint
icon: gift
---

# Lootboxes

## Read all lootboxes

<mark style="color:green;">`GET`</mark> `/lootbox`

Gets all lootboxes in the table

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
        "user_id": 1,
        "lootbox_id": 1,
        "pet_id": 27,
        "opened": 1
    },
    {
        "id": 2,
        "user_id": 3,
        "lootbox_id": 1,
        "pet_id": null,
        "opened": 0
    }
]
```

| Name         | Type              | Descripton                                                    |
| ------------ | ----------------- | ------------------------------------------------------------- |
| `id`         | number            | id of the lootbox                                             |
| `user_id`    | number            | id of the user who bought the lootbox                         |
| `lootbox_id` | number            | id of the type of the lootbox                                 |
| `pet_id`     | number \| null    | id of the pet. if it has not been opened, will return null    |
| `opened`     | number as boolean | 0 if the lootbox has not been opened, if it is open value = 1 |
{% endtab %}
{% endtabs %}

## Buy a lootbox

<mark style="color:green;">`POST`</mark> `/lootbox`

Creates a new lootbox linked to the user. Deducts points from the user specified in the lootbox type.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name         | Type   | Description            |
| ------------ | ------ | ---------------------- |
| `user_id`    | number | id of the user         |
| `lootbox_id` | number | id of the lootbox type |

**Response**

{% tabs %}
{% tab title="201" %}
```json
{
    "id": 8,
    "user_id": 1,
    "lootbox_id": 1,
    "pet_id": null,
    "opened": 0
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "message": "Error: user_id is undefined"
}
```
{% endtab %}

{% tab title="404" %}
```json
{
    "message": "Lootbox not found"
}
```
{% endtab %}

{% tab title="422" %}
```json
{
    "message": "Not enough points for transaction"
}
```
{% endtab %}
{% endtabs %}

## Open a lootbox

<mark style="color:green;">`GET`</mark> `/lootbox/{id}/open`

Changes the state of a lootbox to opened, and creates a new pet linked to the owner of the lootbox. Each lootbox can only be opened once.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Params**

| Name | Type   | Description       |
| ---- | ------ | ----------------- |
| `id` | number | id of the lootbox |

**Body**

```json
{} //Empty body
```

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "id": 4,
    "user_id": 3,
    "lootbox_id": 1,
    "pet_id": 33,
    "opened": 1
}
```
{% endtab %}
{% endtabs %}

