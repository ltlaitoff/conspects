---
title: Destination select
created: 2024-05-09 14:28
last modified: Thursday 9th May 2024 14:28:23
aliases: 
tags: []
---
# Destination select

This documentation explains how the destination selection should work

## Basic concepts

- `Destination` - This is the area in which we want to search for hotels, rooms, and more

## Data that the server works with

You can also view it in swagger: `GeolocationDto`

The backend accepts the following fields:
- `radius` - Radius of circle in kilometers. Used to search offer in circle. maximum: 200; minimum: 0
- `topLeft` - required. This point used to search by dot or rectangle.
	- `latitude` - required. Number. Latitude coordinate for geolocation search.
	- `longitude` - required. Number. Longitude coordinate for geolocation search.
- `bottomRight` - required. This point used to search by rectangle.
	- `latitude` - required. Number. Latitude coordinate for geolocation search.
	- `longitude` - required. Number. Longitude coordinate for geolocation search.

Although we have three fields, the `backend` can accept two destination options:
1. By point with radius - through `radius` and `topLeft` as a point
2. Through a rectangle - through `topLeft` and `bottomRight`

**This documentation only considers the point and radius variant**

## Two fields for selecting destination

On the site, the user has two fields for selecting a destination (hereinafter they will be called `destination select`): in `Main Search` and on the map

**These elements must be synchronized**. That is, when a user selects something in one element - it should also appear in the other

## How the point-based selection should work

Let's consider some examples of how `destination select` works

### Through destination select on main search

When a user selects a city through `main search` `destination select`:
- Its coordinates are recorded in `topLeft`
- The radius remains the same as it was before changing `topLeft`
- The `destination` selected by the user is displayed in `main search` `destination select`

Also, if the map is open:
- `destination select` on the map should show the same `destination` that the user selected
- The map shows a point (coordinates `topLeft`) with a circle (`radius`) along which the search will go

We do not have a mechanism for changing the radius on `main search`

### Through destination select on the map

When a user selects a `destination select` city on the map:
- Its coordinates are recorded in `topLeft`
- The radius remains as it was before the `topLeft` change
- `destination select` on `main search` should show the same `destination` that the user selected on the map
- The map shows a point (coordinates `topLeft`) with a circle (`radius`) along which the search will go

### Changing the radius

Suppose the user has chosen a `destination`, but now he is not satisfied with the radius

**The radius can be changed on the map**

When changing the radius, the circle that visually represents this radius on the map should also change

### Through a point on the map

The user may also want to place a point on the map

The coordinates of this point will be written in `topLeft`

**And in both `destination select` should show an approximate destination to this point**

## How the selection through the rectangle should work

For now, not at all)
