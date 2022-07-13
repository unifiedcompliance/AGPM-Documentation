---
description: >-
  This page provides the details necessary to call each of the account
  management APIs.
---

# API Specification

{% swagger method="get" path="/Account" baseUrl="https://api.complianceascode.net/manage" summary="Retrieve account API specification" %}
{% swagger-description %}

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

{% swagger method="post" path="/Account/add" baseUrl="https://api.complianceascode.net/manage" summary="Add User API specification" %}
{% swagger-description %}

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

{% swagger method="post" path="/Account/invite" baseUrl="https://api.complianceascode.net/manage" summary="Invite User API specification" %}
{% swagger-description %}

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

{% swagger-response status="200: OK" description="Returns the details of the user added to the account.  The Status returned will be "Invited"." %}
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

{% swagger method="post" path="/Account/" baseUrl="https://api.complianceascode.net/manage" summary="Invite User API specification" %}
{% swagger-description %}

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

{% swagger method="get" path="" baseUrl="https://api.complianceascode.net/manage" summary="" %}
{% swagger-description %}

{% endswagger-description %}
{% endswagger %}
