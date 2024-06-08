---
title: How Icons are Displayed
created: 2024-06-04 10:42
last modified: Tuesday 4th June 2024 10:42:29
Aliases:
Tags:

---
# How Icons are Displayed

We have 4 options for which icon to display:
- Option icon. The highest priority option. The `iconName` field determines which icon to display
- Feature icon. Displayed if the option does not have an icon. The `iconName` field determines which icon to display
- Group icon. Displayed if the feature does not have an icon. The `iconName`(`dev-2`) field determines which icon to display
- General icon. Displayed if the group does not have an icon


## How does it all work?

We have a set of icons common to all elements

We have separate icons for groups, separate icons for features, and separate icons for options

Also, the icons for features may depend on which group is selected

That is, we have a hierarchical structure:
`Group -> Feature -> Option`

Option icons depend on the selected feature icons, and feature icons depend on the selected group icons

But, we may have a situation where the group has no icons at all, or the feature has no icons at all

And for such cases, we need a set of standard icons for all features in cases when the group does not have icons

### Examples

#### Example 1

Group: G1
Feature: F1
Option: O1

We take the F1 icon from the G1 icon set, and the O1 icon from the F1 icon set

If F1 is not in G1 - the G1 icon is returned
	If there is no G1 icon - a standard icon is returned
If O1 is not in F1 - F1 is returned
The O1 icon is returned

#### Example 2

Group: -
Feature: F1
Option: O1

Since we don't have a group at all, we take icons from the standard set of feature icons (FSET)

If F1 is not in FSET - a standard icon is returned
If O1 is not in F1 - F1 is returned
The O1 icon is returned

## Sets

Standard set of icons for groups:
- `Accessibility`
- `Beauty and wellness`
- `Business`
- `General`
- `Health and Safety Measures`
- `Internet`
- `Kids`
- `Languages Spoken`
- `Meals`
	- `Meals` feature unique?
- `Parking`
	- `Parking`
- `Pets`
	- `Pets` feature unique?
- `Pool and beach`
- `Recreation`
- `Rooms`
	- `Bathroom` feature unique?
- `Services and amenities`
- `Sports`
- `Tourist services`
- `Transfer`
- `View`
- `Accommodation type`
- `Location`

Standard set of icons for features:
- `Beds`
- `Bathroom`
- `Meals`
