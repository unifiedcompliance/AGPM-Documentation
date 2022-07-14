---
description: >-
  This page provides the details necessary to call each of the account/user
  management APIs, and, to see sample responses.
---

# API Specification

## Manage Account APIs

{% swagger method="get" path="/Account" baseUrl="https://api.complianceascode.net/manage" summary="Retrieve Account" %}
{% swagger-description %}
The account returned will be based upon the API Key sent in the header of the request.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
API Key of the account membership
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns account details and users" %}
```javascript
{
    "success": "boolean",
    "code": "integer",
    "message": "string",
    "data": {
        "accounts_id": "integer",
        "name": "string",
        "domain": "string",
        "organizations_id": "integer",
        "admin": {
            "first_name": "string",
            "middle_name": "string",
            "last_name": "string",
            "email": "string"
        },
        "memberships": [
            {
                "users_id": "integer",
                "status": "string",
                "type": "string",
                "persons_id": "integer",
                "first_name": "string",
                "middle_name": "string",
                "last_name": "string",
                "email": "string",
                "api_key": "string"
            }
        ],
        "balance": "string",
        "addresses": {
            "primary": {
                "address1": "string",
                "address2": "string",
                "city": "string",
                "state_territory_province": "string",
                "postal_code": "string",
                "country_code": "string"
            }
        },
        "phone_numbers": {
            "primary": {
                "phone_number": "string"
            }
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/Account/add" baseUrl="https://api.complianceascode.net/manage" summary="Add User" %}
{% swagger-description %}
The user will be added to the account that matches the API Key sent in the header of the request.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
API Key of the account membership
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="email" %}
Email address of the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="first_name" required="true" %}
First name of the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="last_name" required="true" %}
Last name of the user
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns the details of the user added to the account.  The Status returned will be "Active"." %}
```javascript
{
    "success": "boolean",
    "code": "integer",
    "message": "string",
    "data": {
        "membership": {
            "users_id":"integer",
            "status": "string",
            "type": "string",
            "persons_id": "integer",
            "first_name": "string",
            "middle_name": "string",
            "last_name": "string",
            "email": "string",
            "api_key": "string"
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/Account/invite" baseUrl="https://api.complianceascode.net/manage" summary="Invite User" %}
{% swagger-description %}
The user will be invited to the account that matches the API Key sent in the header of the request.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
API Key of the account membership
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="email" %}
Email address of the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="first_name" required="true" %}
First name of the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="last_name" required="true" %}
Last name of the user
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns the details of the user invited to the account.  The Status returned will be "Invited"." %}
```javascript
{
    "success": "boolean",
    "code": "integer",
    "message": "string",
    "data": {
        "membership": {
            "users_id":"integer",
            "status": "string",
            "type": "string",
            "persons_id": "integer",
            "first_name": "string",
            "middle_name": "string",
            "last_name": "string",
            "email": "string",
            "api_key": "string"
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/Account/activate" baseUrl="https://api.complianceascode.net/manage" summary="Activate User" %}
{% swagger-description %}
The user to be activated will match the API Key sent in the header of the request.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
API Key of the account membership
{% endswagger-parameter %}

{% swagger-parameter in="body" required="false" name="users_id" type="Integer" %}
The User ID of the user
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns the details of the user added to the account.  The Status returned will be "Active"." %}
```javascript
{
    "success": "string",
    "code": "integer",
    "message": "string",
    "data": {
        "membership": {
            "users_id": "integer",
            "status": "string",
            "type": "string",
            "persons_id": "integer",
            "first_name": "string",
            "middle_name": "string",
            "last_name": "string"",
            "email": "string",
            "api_key": "string""
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/Account/remove" baseUrl="https://api.complianceascode.net/manage" summary="Remove User" %}
{% swagger-description %}
The user will be removed from the account that matches the API Key sent in the header of the request.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
API Key of the account membership
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="users_id" type="Integer" %}
The User ID of the user
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns the details of the user removed from the account.  The Status returned will be "Disabled"." %}
```javascript
{
    "success": "string",
    "code": "integer",
    "message": "string",
    "data": {
        "membership": {
            "users_id": "integer",
            "status": "string",
            "type": "string",
            "persons_id": "integer",
            "first_name": "string",
            "middle_name": "string",
            "last_name": "string"",
            "email": "string",
            "api_key": "string""
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/Account/promote" baseUrl="https://api.complianceascode.net/manage" summary="Promote User" %}
{% swagger-description %}
The user from the account that matches the API Key sent in the header of the request will be promoted.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
API Key of the account membership
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="users_id" type="Integer" %}
The User ID of the user
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns the details of the user promoted in the account.  The Type returned will be "Admin"." %}
```javascript
{
    "success": "string",
    "code": "integer",
    "message": "string",
    "data": {
        "membership": {
            "users_id": "integer",
            "status": "string",
            "type": "string",
            "persons_id": "integer",
            "first_name": "string",
            "middle_name": "string",
            "last_name": "string"",
            "email": "string",
            "api_key": "string""
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/Account/demote" baseUrl="https://api.complianceascode.net/manage" summary="Demote User" %}
{% swagger-description %}
The user from the account that matches the API Key sent in the header of the request will be demoted.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
API Key of the account membership
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="users_id" type="Integer" %}
The User ID of the user
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns the details of the user demoted in the account.  The Type returned will be "User"." %}
```javascript
{
    "success": "string",
    "code": "integer",
    "message": "string",
    "data": {
        "membership": {
            "users_id": "integer",
            "status": "string",
            "type": "string",
            "persons_id": "integer",
            "first_name": "string",
            "middle_name": "string",
            "last_name": "string"",
            "email": "string",
            "api_key": "string""
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/Account/refresh" baseUrl="https://api.complianceascode.net/manage" summary="Refresh API Key" %}
{% swagger-description %}
The user from the account that matches the API Key sent in the header of the request will have a new API Key generated.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
API Key of the account membership
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="users_id" type="Integer" %}
The User ID of the user
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns the details of the user that had a new API Key generated.  Copy the api_key in the response and distribute it to the user." %}
```javascript
{
    "success": "string",
    "code": "integer",
    "message": "string",
    "data": {
        "membership": {
            "users_id": "integer",
            "status": "string",
            "type": "string",
            "persons_id": "integer",
            "first_name": "string",
            "middle_name": "string",
            "last_name": "string"",
            "email": "string",
            "api_key": "string""
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

## Manage User APIs

{% swagger method="get" path="/User" baseUrl="https://api.complianceascode.net/manage" summary="Retrieve User" %}
{% swagger-description %}
The user (in a specific account) returned will match the API Key sent in the header of the request.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
API Key of the account membership
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns the details of the user." %}
```javascript
{
    "success": "boolean",
    "code": "integer",
    "message": "string",
    "data": {
            "users_id": "integer",
            "name": "string",
            "first_name": "string",
            "middle_name": "string",
            "last_name": "string",
            "email": "string",
            "persons_id": "integer",
            "contribute_as": "string",
            "terms_accepted": "string",
            "terms_accepted_at": "string"
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="patch" path="/User" baseUrl="https://api.complianceascode.net/manage" summary="Update User" %}
{% swagger-description %}
The API Key sent in the header of the request will determine the user (within a specific account) to update.  
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
API Key of the account membership
{% endswagger-parameter %}

{% swagger-parameter in="body" name="users_id" type="Integer" required="false" %}
The user ID of the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="first_name" required="true" %}
The first name of the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="middle_name" required="true" %}
The middle name of the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="last_name" required="true" %}
The last name of the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" required="true" %}
The email address of the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="persons_id" type="Integer" required="true" %}
The person ID of the user (use GET to retrieve the current value).
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contribute_as" required="true" %}
Send a value of "person", "organization" or "both".
{% endswagger-parameter %}

{% swagger-parameter in="body" name="terms_accepted" %}
Whether the terms have been accepted or not.  Send a value of "true" or "false".
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Updates the user and returns the details." %}
```javascript
{
    "success": "string",
    "code": "integer",
    "message": "string",
    "data": {
        "users_id":"integer",
        "first_name": "string",
        "middle_name": "string",
        "last_name": "string",
        "email": "string",
        "persons_id": "integer",
        "contribute_as": "string",
        "terms_accepted": "string"
    }
}
```
{% endswagger-response %}
{% endswagger %}
