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
 - http
 - CORS
---

# <%* tR += title %>

