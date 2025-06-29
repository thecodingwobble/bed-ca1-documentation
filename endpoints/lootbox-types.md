---
description: API documentation for /lootbox-types
icon: inbox-out
---

# Lootbox Types

## Read all lootbox types

<mark style="color:green;">`GET`</mark> `/lootbox-types`

Returns an array of all the types of lootboxes

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "id": 1,
        "name": "Mystery Crate",
        "cost": 100,
        "description": "A box filled with surprises and rare chances for epic pets."
    }
]
```
{% endtab %}
{% endtabs %}
