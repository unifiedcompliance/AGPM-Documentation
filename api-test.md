# API Test

{% swagger method="get" path="/Account" baseUrl="https://api.complianceascode.net/manage" summary="Returns gateway" %}
{% swagger-description %}
Will contain current account information. It will be in property "organization".  Only the admin key gets the full account membership with user API keys. User keys will get account detail, but without the user API keys.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
API Key of the account membership
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns account detail including" %}
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

{% swagger method="get" path="" baseUrl="app" summary="" %}
{% swagger-description %}

{% endswagger-description %}
{% endswagger %}
