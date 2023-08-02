Task based on Wakatime API Durations - [link](https://wakatime.com/developers#durations)

```ts
interface WakatimeDurationElement {
	time: number // in seconds; start of this duration as UNIX epoch
	project: string // project name
	duration: number // length of time of this duration in seconds
}
```

## Task

Inputs:
- **data**: Array of `WakatimeDurationElement`
- **delay**: number in minutes

Combine records in which the difference between the end of the record (start + duration) and the beginning of a new one is less than **delay** into one

Return new Array of `WakatimeDurationElement` with combined **AND** sorted by time


## Example

Given
```js
data = [{
	time: 1688728147,
	project: 'project1',
	duration: 860
},
{
	time: 1688729300,
	project: 'project1',
	duration: 20
}],
delay = 5
```

Because

project1 `end` = `time` project1 + `duration` project1
project1 `end` = 1688728147 + 860 = 1688729007

project2 `time` - project 1 `end` < delay * 60

1688729300 - 1688729007 < 5 * 60
293 < 300

Return 
```js
{
	time: 1688728147,
	project: 'project1',
	duration: 1173
}
```