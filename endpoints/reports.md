---
description: API documentation for /reports
icon: file-chart-column
---

# Reports

## Create a new report

<mark style="color:green;">`POST`</mark> `/report`

Creates a new report linking a user to a vulnerability. Provide user\_id and\
vulnerability\_id in the request body. The initial status of the report will be set to 0.

Upon successful creation of the report:\
o The report record is added to the Report table.\
o The system will retrieve the points associated with the vulnerability\_id\
from the Vulnerability table.\
o These retrieved points will be added to the reputation and points of the User identified\
by the user\_id in the Report record.\
o The response will include the newly created report details (id, user\_id,\
vulnerability\_id, status). The updated reputation of the user will be included\
in the response for confirmation.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name               | Type   | Description             |
| ------------------ | ------ | ----------------------- |
| `user_id`          | number | Id of the user          |
| `vulnerability_id` | number | Id of the vulnerability |

**Response**

{% tabs %}
{% tab title="201" %}
```json
{
"id": 1, // report id
"user_id": 2, // user who found the bug
"vulnerability_id": 5, // corresponding id in vulnerability table
"status": 0, //the status of the report, 0 for open, 1 for closed
"user_reputation": 100 //the updated reputation after creating the report
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "message": "Error: missing required fields"
}
```
{% endtab %}

{% tab title="404" %}
```json
{
    "message": "Vuln not found" //will change depending on whats missing
}
```
{% endtab %}
{% endtabs %}

## Create a new user

<mark style="color:green;">`POST`</mark> `/users`

Update the status of a specific report by providing the report\_id (matches the id field in Report table) in the URL and the new status (typically 1 to resolve it) in the request body. If the status is updated to 1 (Closed), the points for the associated vulnerability should be added to the reputation of the user specified by the user\_id in the request body. This user\_id represents the user closing the report. It will overwrite the user\_id of the original bug finder.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name      | Type              | Description                          |
| --------- | ----------------- | ------------------------------------ |
| `status`  | number as boolean | Status of the report                 |
| `user_id` | number            | id of the user who closed the report |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
"id": 1, //report id
"status": 1, // indicating report id 1 is closed or resolved
"closer_id": 7, // Explicitly show who closed it
"user_reputation": 150 // Updated reputation of user
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
    "message": "Report not found"
}
```
{% endtab %}
{% endtabs %}
