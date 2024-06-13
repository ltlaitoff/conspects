---
title: UTM
created: 2024-06-13 08:34
last modified: Thursday 13th June 2024 08:34:11
aliases: 
tags: []
---
# UTM

## How they should work

After a user lands on a page with UTM parameters, they should be sent to GA4 via the `page_view` event

![[Pasted image 20240613084242.png]]

**It's important that they should be sent to GA4 only once**

The site should function correctly, i.e., perform searches correctly and display information correctly

Then, when moving to other pages, the UTM should **be removed** from the address bar. This is necessary to avoid duplication in GA4
