# conspects
%% 
<a href="https://www.buymeacoffee.com/ltlaitoff"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=&slug=ltlaitoff&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" /></a> <a href="https://steamcommunity.com/tradeoffer/new/?partner=1117923836&token=OGmuhFb0"><img src="https://png2.cleanpng.com/sh/e19282bb49f411a4eff4b0814fde464f/L0KzQYm3V8E0N5ZngJH0aYP2gLBuTgN1bZJyRdV4bYD4hLb5Tflkd594Rd1ybHzogn74lfVmdl5nhNNsaz35cb39hb1kd6N1Rd54YXSwhLnsTfFvcZ5mjNt4bj24coWCVPM6P2drUalsNj61RYi8Vsk5OWI6S6MAM0C2SYK7VccyNqFzf3==/kisspng-steam-computer-icons-killer-queen-black-valve-corp-load-the-animation-5b494c976f97c6.2575698115315303914571.png" width="69px" /></a>


```dataview
LIST
FROM #book 
```

```tracker
searchType: frontmatter
searchTarget: habbit1, habbit2
folder: 01 - My/daily
dateFormat: DD-MM-YYYY
month:
	mode: annotation
	startWeekOn: 'Mon'
	threshold: 0, 0
	dimNotInMonth: false
	circleColorByValue: true
	annotation: L, D
	showAnnotationOfAllTargets: true
```



# 📓 Recent Journal Entries
```dataview
TABLE rating AS "Rating", summary AS "Summary" 
FROM "01 - My/daily"
SORT file.name DESC
```

```dataviewjs
let pages = dv.pages('"01 - My/daily"')
console.log(file.day)
```

```dataview
TABLE WITHOUT ID file.link AS "File", regexreplace(Tasks.text, "\[.*$", "") AS Task, choice(Tasks.completed, "✔️", "❌") AS Status

FROM "01 - My/daily" 
WHERE file.tasks
FLATTEN file.tasks AS Tasks
```

```dataview
TABLE WITHOUT ID file.link AS "File", regexreplace(Tasks.text, "\[.*$", "") AS  "Medination mornig", "Back training morning"
FROM "01 - My/daily" 
WHERE file.tasks
FLATTEN file.tasks AS Tasks
``` %%

```dataview
TABLE WITHOUT ID
	link(file.name) as "Day",
	choice(filter(file.tasks, (t) => t.habit = "mediatation morning").completed, "✔️", "❌") AS "mediatation morning",
	choice(filter(file.tasks, (t) => t.habit = "back training morning").completed, "✔️", "❌") AS "back training morning",
	choice(filter(file.tasks, (t) => t.habit = "mediatation evening").completed, "✔️", "❌") AS "mediatation evening",
	choice(filter(file.tasks, (t) => t.habit = "back training evening").completed, "✔️", "❌") AS "back training evening",
	FROM "01 - My/daily" 
	WHERE file.cday.day >= 21
	SORT file.name DESC
```