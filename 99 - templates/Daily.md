<%*
	let title = tp.file.title
	
	if (title.startsWith('Untitled')) {
		title = tp.file.creation_date("DD-MM-YYYY")
		await tp.file.rename(title)
	}
%>---
title: <%* tR += title %>
created: <% tp.file.creation_date("DD-MM-YYYY") %>
last modified: <% tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %>
aliases: 
tags:
  - daily
---
# <%* tR += title %>
## Що б я хотів виправити в цьому дні, щоб він став краще?

- 

## Що я можу зробити прямо зараз або до кінця дня, щоб він став краще?

- 
