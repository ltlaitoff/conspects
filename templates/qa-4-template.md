<%*
	let title = tp.file.title
	
	if (title.startsWith('Untitled')) {
		title = await tp.system.prompt('Title')
		await tp.file.rename(title)
	}
	
%>---
title: <%* tR += title %>
created: <% tp.file.creation_date() %>
Aliases:
Tags: 
 - testing
 - QA-DL-Academy
 - QA-Lecture-14_Менеджмент-тестування
---

# <%* tR += title %>

