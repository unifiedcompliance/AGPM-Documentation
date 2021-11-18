# API Reference

We are in early alpha and kicking off documentation. This is what you need to know right now.

{% swagger src=".gitbook/assets/result.yml" path="undefined" method="undefined" %}
[result.yml](.gitbook/assets/result.yml)
{% endswagger %}

1. Get Account - Will contain current account information AND a NEW linked grcschema Organization object. (the full object). It will be in property "organization". We also specifically provide the Admin user information for the account in the property "admin". Only the admin key gets the full account membership with user API keys. User keys will get account detail, but without the user API keys.
2. Post Account/add (user) - Adds a user to the account without an invite. (this effectively bypasses the invite process) The API key for the user membership will be active and the user can immediately leverage the key to make calls.
3. Post Account/activate (user) - Will change a user's membership status to "active" regardless of the current status.
4. Post Account/remove (user) - Will change any user's membership status to "disabled". With the exception of the admin-user making the request.
5. Post Account/invite (user) - Will add a user with an invited membership status and will need to be activated upon acceptance (by user as you see fit).
6. Post Account/approve and Post Account/deny - Specifically looks for membership status 5 (Requested) and approve makes the user "active" and deny makes the user "declined". These endpoints are important when a user at the api gateway platform web application requests to join an account. (we will have a webhook later that you can subscribe to by account to receive notification of a request).
7. Post Account/promote - Will no longer promote an existing admin, but will promote any active user with an account membership to the admin role. The current admin WILL ALSO stay an admin. (we are going to support multiple admins now - for backup administration etc)
8. Post Account/demote - Will demote an admin to a regular user. With the exception of the admin-user making the request.
9. Get /User
