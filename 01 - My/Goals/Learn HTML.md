---
Description: 
Why: 
---

```dataview 
LIST without ID
	"**" + this.file.name + "**<br> " + "<progress value='" + (length(filter(this.file.tasks.completed, (t) => t = true)) / length(this.file.tasks)) * 100 + "' max='100'></progress>" + "<br>" + round((length(filter(this.file.tasks.completed, (t) => t = true)) / length(this.file.tasks)) * 100) + "% completed"
FROM "01 - My/Goals"
LIMIT 1
```

# Tasks

- [ ] Task 1
- [ ] Task 2