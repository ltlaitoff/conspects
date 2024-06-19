<%*
	let title = tp.file.title
	
	if (title.startsWith('Untitled')) {
		title = await tp.system.prompt('Title')
		await tp.file.rename(title)
	}
%>---
title: <%* tR += title %>
created: <% tp.file.creation_date() %>
last modified: <% tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %>
aliases:
tags:
  - book/you-dont-know-js/scope-and-closures

---
# <%* tR += title %>
