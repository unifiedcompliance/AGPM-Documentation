---
description: Utilize REST-based APIs to manage your account.
---

# Gateway API Reference

The Unified Compliance API gateway provides several APIs that you can utilize to manage your account (effectively performing the same administrative functions you would do using the API Gateway web-based interface).  Specifically, you can:

* Retrieve all users on the account, including account information
* Add a user to an account&#x20;
* Invite a user to an account
* Activate a user in an account
* Remove a user in an account
* Promote a user in an account
* Demote a user in an account
* Refresh the API Key for a user in an account

In addition, Users can perform the following operations on their User accounts:

* Retrieve a specific user in an account
* Update a specific user in an account

Let's take a closer look at the details of each of these APIs below.

## Manage Account APIs

#### Retrieve All Account Data

Reference the API Specification here:  [#retrieve-account](api-test.md#retrieve-account "mention")

This API takes a GET request where the API Key in the header will determine the account to return in the response.  The API response will contain the Account ID, Account Name, Account Domain, Organization ID, the Account token balance, an array of Account Addresses, an array of Account Phone Numbers, and an array of Users.  If this API call is made utilizing an Admin API key, then the API key of each user will be returned in the array of users.  If a regular User (non-admin) makes this  API call, then the API key of each user in the account will not be returned. &#x20;

#### Add User to Account

Reference the API Specification here:  [#add-user](api-test.md#add-user "mention")

This API takes a POST request where the API Key in the header will determine the account to add the user to.  And in the POST body, send the First Name, Last Name, and Email Address of the user to add.  This operation adds the user to the account without an invitation, the membership is immediately active, and the API Key generated for the user can be used immediately to make API calls.&#x20;

#### Invite User to Account

Reference the API Specification here:  [#invite-user](api-test.md#invite-user "mention")

This API takes a POST request where the API Key in the header will determine the account the user will be added to.  And in the POST body, send the First Name, Last Name, and Email Address of the user to add.  This operation will add a new user to the account with an "invited" membership status.  Once your user (manually) accepts the invitation, the user will need to be activated via the Activate User API call.

#### Activate User in Account

Reference the API Specification here: [#activate-user](api-test.md#activate-user "mention")

This API takes a POST request where the API Key in the header will determine the user and account to update.  And in the POST body, send the User ID of the user to activate.  This operation will change a user's membership status to "active" regardless of the current status.

#### Remove User from Account

Reference the API Specification here: [#remove-user](api-test.md#remove-user "mention")

This API takes a POST request where the API Key in the header will determine the user and account to remove (disable).  And in the POST body, send the User ID of the user to remove.  This operation will change the user's membership status to "disabled" (with the exception of the admin-user making the request). &#x20;

#### Promote User in Account

Reference the API Specification here: [#promote-user](api-test.md#promote-user "mention")

This API takes a POST request where the API Key in the header will determine the user and account to promote.  And in the POST body, send the User ID of the user.  This operation promotes an active User on the account to an Admin.   An account may have several Admin users (as needed to manage the account). &#x20;

#### Demote User in Account

Reference the API Specification here: [#demote-user](api-test.md#demote-user "mention")

This API takes a POST request where the API Key in the header will determine the user and  account to demote.  And in the POST body, send the User ID of the user.  This operation demotes an active Admin user to a regular user by setting the Type to "User" (with the exception of the admin-user making the request).

#### Refresh User API Key in Account

Reference the API Specification here: [#refresh-api-key](api-test.md#refresh-api-key "mention")

This API takes a POST request where the API Key in the header will determine the user and account to generate a new API Key.  And in the POST body, send the User ID of the user.  This operation generates a new API key for the user in the account (and the old API Key can no longer be used for making API calls). &#x20;

## Manage User APIs

#### Retrieve User from Account

Reference the API Specification here:[#retrieve-user](api-test.md#retrieve-user "mention") &#x20;

This API takes a GET request where the API Key in the header will determine the user (in the account they belong to) to return in the response.  The API response does not contain membership information such as the API Key. However, it will contain the User ID, first name, middle name, last name, email address, person ID, contribute as, terms accepted, and the date/time the terms were accepted. &#x20;

#### Update User in Account

Reference the API Specification here:[#update-user](api-test.md#update-user "mention")

This API takes a PATCH request where the API Key in the header will determine the user and account to update.  And in the PATCH body, send the First Name, Middle Name, Last Name, Email Address, Person ID, and Contribute As values to update.  The User ID and Terms Accepted elements are optional. &#x20;

Enum values for Contribute\_As: person, organization, both. &#x20;

Enum values for Terms\_Accepted: true, false &#x20;

