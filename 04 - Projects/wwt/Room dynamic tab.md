---
title: Room dynamic tab
created: 2024-05-30 10:23
last modified: Thursday 30th May 2024 10:23:00
aliases: 
tags:
  - winwintravel
---
# Room dynamic tab

The list of feature groups that we get from BE will be totally dynamic

We want to have the ability to generate room offer tabs dynamically too

For that we will change `group` field from string to object(feature group DTO) in another(see blocked) tasks:
```ts
interface FeatureGroupDTO {
	name: string
	tabName: string
	iconName: string
}
```

What need to do in this task?

All hotel and room features show on room tab
All hotel features show on hotel tab
On location tab show only features where `tabName` is `location`

On all other `tabName` need create dynamic page with feature only from this tab grouped by group name