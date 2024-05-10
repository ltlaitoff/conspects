---
title: Brevo
created: 2024-05-09 12:42
last modified: Thursday 9th May 2024 12:42:44
aliases: 
tags: []
---
# Brevo

This documentation describes how to test `brevo` - a system for collecting statistics

## Prerequisites

You should have access to `brevo` for testing, if you don't have it - contact Vadim

## Description of entities

`Brevo` is a fairly simple system, which consists of two main entities:
- `Contact` - a single record, can be imagined as a record in a database or a row in a table
- `List` - a list that can contain contacts

There is an important nuance in that the contact does not belong to the list, but is a separate global entity. What does this mean?
1. A contact can belong to several lists at the same time
2. If we try to create a contact with mail (see below the contact parameters) in some list, but there is already a contact with the same mail somewhere, we will get an error (except for some situations, which will be described later)

### Contact

The contact has the following **important** fields:
- `EMAIL` - The most important field. User's mail
- `REQUEST_DISCOUNT_VALUE` - Data from *request discount modal*
- `NPS_RESPONSE` - Data from the text field `nps` modal
- `NPS_SCORE` - Rating data from `nps` modal

### List

In `brevo` we have the following lists:
- `LoginMobile` - Contacts of people who registered from a phone or tablet
- `Login` - Contacts of people who registered from a computer
- `NPS` - Requests for site evaluation
- `discountRequests` - Records of discount requests
- `Langing` - Contacts from the landing. They are not very necessary to us

## Usage

### Login

When a user enters an email from a computer, a new contact is added to the `Login` list if there is no contact with such an email, **or an existing contact is added to this list**

`LoginMobile` works in exactly the same way

At the same time, the `NPS_*` and `REQUEST_DISCOUNT_VALUE` fields are not used

### NPS

When a user sends an `NPS` modal, a new contact of the following format is created in the `NPS` list:
- email: `{timestamp}-{email}` 
- nps_response: `{text}`
- nps_score: `{number}`

! Why record such a format in email? This is necessary to create a completely new and unique contact, so that we can track the user's history, since at different times the user may choose different `score`

## Request discount

When the user sends a `Request discount` modal, a new contact is created in the `discountRequests` list in the format:
- email: `{timestamp}-{email}` 
- REQUEST_DISCOUNT_VALUE: `{json}`

Why the `email` has such a format was described in `NPS`

Why is `REQUEST_DISCOUNT_VALUE` recorded in `json` format? Because we need to save many fields at once and this is the best option available.
