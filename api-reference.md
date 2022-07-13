---
description: Utilize APIs to manage your account
---

# API Reference

The Unified Compliance API gateway provides several APIs that you can utilize to manage your account (effectively performing the same administrative functions you would do using the API Gateway web-based interface) .  Specifically, you can:

* Retrieve all users on the account including account information
* Retrieve a specific user on an account
* Update a specific user on the account
* Add a user to an account&#x20;
* Invite a user to the account
* Activate / Remove a user on the account
* Approve / Deny a user that requested to join the account
* Promote / Demote a user on the account
* Refresh the API Key for a user on the account

Let's take a closer look at each of these APIs below.

#### Retrieve All Account Data&#x20;

[#retrieve-account-api-specification](api-test.md#retrieve-account-api-specification "mention")

This API takes a GET request where the API Key in the header will determine the account to return in the response.  The API response will contain the Account ID, Account Name, Account Domain, Organization ID, the Account token balance, an arrays of Account Addresses, an array of Account Phone Numbers, and an array of Users.  If this API call is made utilizing an Admin API Key, then the API key of each user will be returned in the array of users.  If a regular User (non-admin) makes this  API call, then the API key of each user on the account will not be returned. &#x20;

#### Add User to Account

[#add-user-api-specification](api-test.md#add-user-api-specification "mention")

This API takes a POST request where the API Key in the header will determine the account to add the user to.  And in the POST body, send the First Name, Last Name, and Email Address of the user to add.  This operation adds the user to the account without an invitation, the membership is immediately active, and the API Key generated for the user can be used to make API calls.&#x20;

#### Invite a User

[#invite-user-api-specification](api-test.md#invite-user-api-specification "mention")

This API takes a POST request where the API Key in the header will determine the account the user will be added to.  And in the POST body, send the First Name, Last Name, and Email Address of the user to add.  This operation will add a new user to the account with an "invited" membership status.  Once your user accepts the invitation, the user will need to be activated.

#### Retrieve a User

This API takes a GET request where the API Key in the header will determine the user/account to return in the response.  The API response does not contain membership information, however, it will contain the user ID, first name, middle name, last name, email address, person ID, contribute as, terms accepted, and the date/time the terms were accepted. &#x20;

#### Update a User

This API takes a PATCH request where the API Key in the header will determine the account the user will be updated in.  And in the PATCH body, you just send the user ID, and optionally one or more of these fields to update:  First Name, Middle Name, Last Name, Email Address, Person ID, Contribute As, and Terms Accepted. &#x20;

#### Activate a User

This API takes a POST request where the API Key in the header will determine the account the user is in.  And in the POST body, send the user\_id of the user to activate.  This operation will change a user's membership status to "active" regardless of the current status.

#### Remove a User

This API takes a POST request where the API Key in the header will determine the account the user is in.  And in the POST body, send the user\_id of the user to remove.  This operation will change any user's membership status to "disabled" (with the exception of the admin-user making the request). &#x20;

#### Approve a User

This API takes a POST request where the API Key in the header will determine the account the user belongs to.  And in the POST body, send the user\_id of the user.  Note:  This API relies on a "request to join account" API that currently is not published.  This operation looks for a membership status of "5" (requested to join) and sets the status of the user in the account to "active".

#### Deny a User

This API takes a POST request where the API Key in the header will determine the account the user belongs to.  And in the POST body, send the user\_id of the user.  Note:  This API relies on a "request to join account" API that currently is not published.  This operation looks for a membership status of "5" (requested to join) and sets the status of the user in the account to "declined".   &#x20;

#### Promote a User

This API takes a POST request where the API Key in the header will determine the account the user belongs to.  And in the POST body, send the user\_id of the user.  This operation promotes an active User on the account to an Admin.   An account may have several Admin users (as needed to manage the account). &#x20;

#### Demote a User

This API takes a POST request where the API Key in the header will determine the account the user belongs to.  And in the POST body, send the user\_id of the user.  This operation demotes an active Admin user to a regular user (with the exception of the admin-user making the request).

#### Refresh a User's API Key

This API takes a POST request where the API Key in the header will determine the account the user belongs to.  And in the POST body, send the user\_id of the user.  This operation generates a new API key for the user in the account (and the old API Key van no longer be used). &#x20;

#### License

_**MORE INFO HERE -**_ License - what to do here?   Also, Post Generate Request Token?

To learn about the URIs and see actual JSON responses for each of these APIs, visit the next section of this guide.
