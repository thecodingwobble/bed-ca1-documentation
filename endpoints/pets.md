---
description: API documentation for /pets
icon: paw
---

# Pets

## Read a pet

<mark style="color:green;">`GET`</mark> `/pets/{id}/all`

Returns all the pet info specified by the id

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Params**

| Name | Type   | Description   |
| ---- | ------ | ------------- |
| `id` | number | id of the pet |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "pet_id": 1,
    "owner_id": 1,
    "dex_num": 4,
    "experience": 0,
    "rarity_name": "Common",
    "weight": 50,
    "multiplier": 1,
    "petdex_name": "Redirect Rabbit",
    "type1": 4
}
```
{% endtab %}

{% tab title="404" %}
```json
{
    "message": "Pet not found"
}
```
{% endtab %}
{% endtabs %}

## Update a pet

<mark style="color:green;">`PUT`</mark> `/pets/{id}`

Updates the fields of a pet, and returns the modified record.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name         | Type   | Description                             |
| ------------ | ------ | --------------------------------------- |
| `user_id`    | number | id of the user its associated with      |
| `rarity_id`  | number | Id of the rarity the pet has            |
| `experience` | number | amount of experience points the pet has |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "id": 1,
    "owner_id": 2,
    "dex_num": 4,
    "rarity_id": 3,
    "experience": 875
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "message": "Error: user_id, rarity_id, experience is undefined"
}
```
{% endtab %}

{% tab title="404" %}
```json
{
    "message": "Pet not found"
}
```
{% endtab %}
{% endtabs %}
