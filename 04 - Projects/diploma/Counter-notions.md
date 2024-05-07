## Categories table

Create a `group` table column

By default group should be `-` with gray bg or not be

In group-cell:

- Group name with bg
- On hover should have `x` button for delete from category (on click call `CategoryAction.change`)

On click on group-cell should be show group-menu:

- In top should be choise group:
  - Control button:
    - On drag - reorder `(GroupsActions.reorder)`
    - On click - call menu with edit and delete fields
      - On delete - delete `(GroupsActions.delete)`
      - On edit - call edit form `(GroupsActions.change)`
  - Text group with bg
    - On click add category group `(CategoryAction.change)`
  - In bottom add group button
    - On click call add group form with one field `group name`. `(GroupsActions.add)`

If group has been ... and not-sync:
created:

- Not allow set to category
- Not allow to edit or something
  changed:
- Change local and show not-sync icon
  deleted:
- Remove from all categories where it group uses
- In bottom of the list choice group create not-sync delete group with bg-gray and disabled
  reordered:
- Show as not-sync

## Category select

In category-select component created tabs:

- Category(default):
  Its current view
- Group:
  Create open/close functional(as `<details>` html tag)
  On open show categories that belong to this group
  Not show add button
  Search must be working(auto open groups and highlights categories)

## Resolver

- Create new GroupResolver

## API

Model:

```ts
type IGroup = {
  name: string;
  user: ObjectId; // Connected to User
};
```

New routes `/groups`:
GET `/group/all` - Get groups
POST `/group/add` - Add new group
Body: `{name: string}`
PUT `/group/change` - Change group
Body: `{name?: string}`
DELETE `/group/delete/:id` - Delete group

Add in `Category` new `group?: ObjectId` field
Update `dto's`
