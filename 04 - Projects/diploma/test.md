# Category time

## Backend

Add in category `type` field. By default `type` = `number`

```ts
type: 'number' | 'time'
```

Category type `time` is meaning `statistic` count field its seconds

### helpers

Migrate functions:
- Create `addForAllCategoriesTypeField` for add for all categories `type` field = 'number'
- Create `tranformMyStatisticToTimeAsSeconds`  :)

## Frontend

### Categories

In categories table add column for type current category

In `add/edit` form add field for choice category type

On change category type from `number` to `time` or from `time` to `number` just not touch, all good

### Home page

By standart on category not choiced input is number

On choice `number` category - not touch
On choice `time` category - transform number as second to time

On change from `time` to `number` transform `time` to `number` as seconds

### Statistic

Add button for choice current graph type: `all` or `only numbers` or `only time`

In `all` visualize `time` as {minutes}.{seconds} without coef **OR** try solve it using chart.js [multi-axis](https://www.chartjs.org/docs/latest/samples/line/multi-axis.html)

In `only numbers` visualize only numbers as standart

In `only time` use y-axis as chart.js `time` 

In `category` | `group` choice add `category with types` for create graphs of different type diff colors