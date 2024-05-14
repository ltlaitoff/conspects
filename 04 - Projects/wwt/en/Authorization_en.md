---
title: Authorization
created: 2024-05-14 11:25
last modified: Tuesday 14th May 2024 11:25:52
aliases: 
tags: []
---
# Authorization

This documentation describes how our authorization works in interaction with the backend.

## Registration

First, we need to register a user by sending a request with an email (which the user enters the Login field of the modal) and a password (currently this is a hard-coded string).

If the user is not registered - the backend should return us a 201 status and the data of the new user.

If the user is already registered - the backend should return us a 200 status and the user's data, and also should indicate somewhere that this user is already registered.

## Authorization

After registration, we need to authorize - for this, we make a request with the same email and password.

If the authorization was successful - we are returned a 200 code and the user's data with a token, by which we will make requests. Also, the tokens expire date is returned.

If the authorization does not work correctly - we are returned a 403 error code, and it is indicated what exactly the error is.

## Automatic reauthorization

When the token expires OR the backend is redeployed, every request to the backend returns a 401 error code.

When our system sees a 401 error code, we first make a registration request, and then an authorization request.

Why so? Why can't we just make an authorization request?

Because during the redeployment, the backend completely resets the databases and all users disappear.
