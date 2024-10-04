---
tags:
  - "#dailynotes"
  - "#resource"
Created: <% tp.file.creation_date("YYYY-MM-DD") %> 
Links:
  - "[[Daily Notes]]"
---

<%*
// templater is having issues with the daily quote service, so this is a workaround:

const jsonUrl = "https://api.allorigins.win/get?url=https://zenquotes.io/api/random";

let response = await fetch(jsonUrl);
let json = await response.json(); // Parsing the outer JSON object
let obj = JSON.parse(json.contents); // Parsing the inner JSON contents

let quote = obj[0].q;
let author = obj[0].a;

// Format the output according to your requirements
tR += `> [!quote] "${quote}" - ${author}`;
%>

---



---
### Notas criadas neste dia
```dataview
LIST 
WHERE file.cday = date(this.file.name)
```