---
description: API documentation for /pets
icon: paw
---

# Pets

## Upgrade a pet

<mark style="color:green;">`PUT`</mark> `/pets/{id}`

Adds the experience of a pet by the inputted amount and subtracts said amount from the user's points, and returns the modified record along with the updated balance of the user. JWT authentication is required.

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | JWT bearer token   |

**Body**

| Name         | Type   | Description                                  |
| ------------ | ------ | -------------------------------------------- |
| `experience` | number | amount of points spend to upgrade experience |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "petData": {
    id: 8,
    dex_num: 4,
    rarity_id: 3,
    rarity_name: 'Rare',
    multiplier: 1.5,
    type1: 4,
    vuln_type: 'Open Redirect',
    type_name: 'Redirect Rabbit',
    experience: 20
  },
  "userData": { id: 4, points: 41140 }
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

## Read a pet <mark style="color:$danger;background-color:$danger;">DEPRECIATED</mark>&#x20;

{% hint style="danger" %}
#### DEPRECIATED

This endpoint is depreciated, and WILL NOT work anymore for CA2.&#x20;
{% endhint %}

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
