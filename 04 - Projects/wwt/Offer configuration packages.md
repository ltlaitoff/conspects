---
title: Offer configuration packages
created: 2024-06-27 17:54
last modified: Thursday 27th June 2024 17:54:34
Aliases:
Tags:

---
# Offer configuration packages


feature 3:
option 3: package 3, package 1 - selected
option 2: package 2

feature 5:
option 5: package 5, package 1 - selected
option 4: package 4, package 2


FMT.ST
1741019108

feature 1:
option 1: package 1 | selected

feature3:
option 3: package 1, package 3 | selected
option 2: package 2



```
  "bookablePackagedFeatures": [
    {
      "name": "bookable packaged feature name 1",
      "options": [
        {
          "name": "packaged option name 1",
          "packages": [
            {
              "bookingKey": "fakePackageKey1",
              "price": 222.5,
              "isSelected": true
            }
          ],
          "isExist": true,
          "isSelected": true
        }
      ]
    },
    {
      "name": "bookable packaged feature name 3",
      "options": [
        {
          "name": "packaged option name 3",
          "packages": [
            {
              "bookingKey": "fakePackageKey3",
              "price": 275.5,
              "isSelected": false
            },
            {
              "bookingKey": "fakePackageKey1",
              "price": 222.5,
              "isSelected": true
            }
          ],
          "isExist": true,
          "isSelected": true
        },
        {
          "name": "packaged option name 2",
          "packages": [
            {
              "bookingKey": "fakePackageKey2",
              "price": 257.5,
              "isSelected": false
            }
          ],
          "isExist": true,
          "isSelected": false
        }
      ]
    }
  ]
```