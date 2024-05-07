# WinWinTravel frontend plan

## Deadline 

Deadline - 04/06/2024

## Goal

Our goal is to create an MVP of a hotel booking website.

The user should be able to enter, find hotels by filtering/sorting, view information about the hotel and if they like it - like it.

After liking, the user should be able to compare different hotels with each other in a large table.

The MVP should work correctly on a computer, meaning it may not be adaptive, but it should be fully tested.

Also, the website should have automatic statistics collection.

### Why are we doing this?

This will allow us to collect people's feedback and understand where to move the project further based on it.

### What should be there

All pages should have the necessary functionality described below.

All pages should have a design as in the layout.

All pages should be tested.

## Main blocks and tasks 

Filtering and sorting
Receiving offer data and displaying it
Likes that are stored on the server
Dislikes that are stored on the server
Display of liked offers in the table

Home page
Comparison page
Offer view page
- Tab with hotel information
- Tab with room information
- Tab with location
- Tab with similar offers
- Tab with rules
Page of viewing the offer only liked
Offer setting
Possibility to request a personal discount

## Application blocks

### Statistic

Google statistic

### Global

We should have basic icons for features

/ QUESTION: ? /
We won't write the name of all groups in caps, will we? Maybe it needs to be hardcoded?

### Header

Logo, clicking on which redirects to the main page

Share with the display of main links

Notification - add feature in dev

Transition to the comparison page if there are likes
- Change the icon
- Remove cursor pointer when hovering if there are no elements
- When clicked if there are no elements - show tooltip first like
- When hovering over the base, show "Transition to the comparison page"

Language change - add feature in dev
Profile - add feature in dev

Mini version of the header that will also be fixed when scrolling like MainSearch

Synchronized design with the layout

Create test cases for the header
Create e2e tests for the header

### Footer

Display of the logo as in the design
Links to the resources we need
All rights reserved

Synchronized design with the layout

Create test cases for the footer
Create e2e tests for the footer

### Main Search

Ability to choose a destination
Ability to choose dates
Ability to choose the number of guests
Ability to choose custom filters
Ability to choose quick filters

Synchronized design with the layout

Create test cases for mainSearch
Create e2e tests for mainSearch

### Home page

Display of offers
Loading additional offers through pagination
The data we send should also be duplicated in URLSearchParams. When the page is refreshed, this data should be set as default
Ability to like/dislike offers locally
Ability to like/dislike offers through API
Map on the main page
Highlighting the offer when clicking on the map tag
Sorting of elements

Synchronized design with the layout

Create test cases for HomePage
Create e2e tests for HomePage

### Room offer page

This page should display search results
If this is the first visit to the page - a request to the API should be made to retrieve data
The data we send should be stored in URLSearchParams, as on the home page, and when first visiting the page, we should make a request for them

The page should have the functionality of moving through offers + additional requests for retrieval if the page has ended

The page should have a slider with pictures
The picture slider should also have different groups of pictures that it displays

The page should have brief information about the offer

On the page in the brief information there should be a working button to open the room offer configuration

On the page in the brief information there should be a working button to open the personal discount request

There should be a Reserve button to which you need to add in dev

Synchronized design with the layout

TODO:
Swap the room and hotel tabs 

Create test cases for the offer page
Create e2e tests for the offer page

#### Room Tab

Display of the hotel name and brief information about it
Display of room features grouped by groups

Highlighting some features that mean that you can click on them and the room offer configuration will open where this can be configured

There should be a Reserve button to which you need to add in dev

Synchronized design with the layout

Make test cases on the tab
Make e2e tests on the tab
#### Hotel Tab

Display of hotel stars
Display of the hotel name
Display of hotel reviews x/10
Brief description

Included features in the form of text

/ QUESTION: ? /
Display of room features grouped by groups

A small map with the display of the hotel position

There should be a Reserve button to which you need to add in dev

Synchronized design with the layout

Make test cases on the tab
Make e2e tests on the tab

#### Location Tab

Display of a large map with the location of the hotel

Display of features that have a LOCATION group

There should be a Reserve button to which you need to add in dev

Synchronized design with the layout

Create test cases for the tab
Create e2e tests for the tab

#### Other rooms tab

Display of similar rooms to this one through an additional search query

Design synchronized with the layout

Create test cases for the tab
Create e2e tests for the tab

#### Rules tab

Display of features that have a RULES_POLICIES_PAYMENT group

There should be a Reserve button that needs to be added in dev

Design synchronized with the layout

Create test cases for the tab
Create e2e tests for the tab

### Room offer configuration

It should be and open when clicking on the button on room-offer
// TODO

Design synchronized with the layout

Create test cases for room offer configuration
Create e2e tests for room offer configuration

### Comparison table

The comparison page should be
The table should display information about liked offers taken locally
The table should display information about liked offers taken from the server
Features should be sorted
There should be sorting within the line by option
There should be a modal for turning off/on features that should be displayed
When scrolling horizontally, icons should be shown
- Display of sorts with icons?
When clicking on removing an offer from the table, the offer should be unliked locally
When clicking on removing an offer from the table, the offer should be unliked on the server
There should be an opportunity to open a map on the page
There should be a map on the page
When clicking on the map tag, the necessary column should be highlighted

When clicking on the hotel or room name - a redirect to the Room offer page where only liked ones will be displayed

Add in dev to the large drop-down in the comparison header
Add in dev to the button in comparison

other:
- Some features will be highlighted
- When hovering over these features, a large tooltip will be displayed
- When clicked - the room configuration opens where you can configure features

Synchronized design with the layout

Make test cases for the comparison table
Make e2e tests for the comparison table

### Request personal discount

It should be and open when clicking on the button on the room-offer
// TODO

Synchronized design with the layout

Make test cases for request personal discount
Make e2e tests for request personal discount

## What we need for MVP

For the release, we need approval from designers that everything is beautiful and clear
And we also need a fully tested basic functionality

## Testing

We need to have test cases for all the basic functionality of the application

Documentation on what a test case is and examples - link // IN DEV

For e2e tests we will use playwright

## Deployment

What's the problem with what we have now? The problem is that considering the speed of development, deployments need to be done every day or two.

Right now, to deploy, you need to manually push a docker image to dockerhub and write in be. If I write to be every day about the need to redeploy, sooner or later everyone will get tired of it.

Solution options:
1. The simplest option. You can host this on vercel, as I did demos, updating every day or two.
2. Make ci/cd. With each push to dev, the project is rebuilt and a deploy is made to something like dev-winwinjs.jstuffs.com or something like that.
3. Make ci/cd not on dev, but on staged and update the staged branch every day - 2, but well, that's something.
4. Connect vercel directly?
