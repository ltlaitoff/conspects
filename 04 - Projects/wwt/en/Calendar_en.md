---
title: Calendar
created: 2024-05-14 06:51
last modified: Tuesday 14th May 2024 06:51:44
aliases: 
tags: []
---
# Calendar

## General Information

The calendar can be divided into: the calendar itself, the modal in which it is rendered, and the control buttons for it.

The modal is a standard Chakra UI modal. Just a place for rendering the calendar, nothing more.

The calendar itself provides the ability to select dates (the logic of this is described below), the ability to switch between different days, and more.

The control buttons provide the ability to choose one of three operating modes:
- `Exact date` - (default) Search for the exact dates written here.
- `+- days` - (disabled) Search for the dates entered by the user, but +- the number of days also indicated by the user. This functionality is currently not supported by the backend, so it is disabled.
- `Number of days in the period` - (disabled) I have no idea how it should work.

It is important to understand that the calendar can be used separately from the buttons, just as the buttons can be used separately from the calendar.

### How data is sent to the backend

To send the data we selected in the calendar to `searchRequest` (this is what we call the data that is sent to the backend and is used for the search), we write the following:

```tsx
{
  ...otherSearchRequestParams,
  stay: {
    defaultStayPeriod: {
      checkIn: "2024-01-10" // First date from calendar
      checkOut: "2024-01-16" // Second date from calendar
    }
  }
}
```

As we can see, there is no information about the mode selected through the calendar control buttons. Therefore, these buttons are disabled.

## Date selection logic

When we have no dates:
- We select one

When we have one date(`date1`):
- If the user selects a date(`date2`) that is greater than `date1` - `date2` becomes the end of the range, and `date1` is the beginning
- If the user selects a date(`date2`) that is less than `date1` - `date2` becomes the beginning of the range, and `date1` is the end

When we already have a range, we should give the person the opportunity to extend the range
- If the user selects a date(`date2`) that is less than the date currently at the beginning of the range(`date-start`), then we overwrite the start date of the range to `date2`
- If the user selects a date(`date2`) that is greater than the date currently at the end of the range(`date-end`), then we overwrite the end date of the range to `date2` (i.e., we extend the end of the range once)

If a person **IN A ROW** extends the end or the beginning twice, we only put one point

When the user clicks in the middle of the range here the result depends on which last element the user chose.

If the user clicks inside the range for the first time:
- If the user last chose the start date (`start`), then the date the user clicked becomes the end date of the range
- If the user last chose the end date (`end`), then the date the user clicked becomes the start date of the range

If the user clicks inside the range for the n-th time **in a row**:
- If the user last time changed the start date, then the date the user clicked becomes the end date of the range
- If the user last time changed the end date, then the date the user clicked becomes the start date of the range

## Other

We should not show the previous month from the current one
We should show a maximum of 12 months from the current one

The dates in the input poll should only be updated if we have a correct range of two dates

## How to test all this

How to test the calendar from scratch:
1. Go to the production or development site
2. If we have default data set - in URLSearchParams you need to delete `stay.defaultStayPeriod.checkOut` and `stay.defaultStayPeriod.checkIn` parameters
3. Refresh the page
4. Click around

Example:
https://winwin.jstuffs.com/?flagSearch.isSearchWithOfferDynamicData=true&flagSearch.isSearchWithHotelStaticData=true&flagSearch.isSearchWithRoomStaticData=true&pagination.limit=12&pagination.offset=0&sortBy=PRICE_ASC&geolocation.radius=200&geolocation.topLeft.latitude=52.377956&geolocation.topLeft.longitude=4.89707&guestQuantity.adultsQuantity=2&integrationSearch.integrationName=FAKE_INTEGRATION
