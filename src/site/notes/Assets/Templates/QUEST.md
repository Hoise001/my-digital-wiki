---
{"dg-home":false,"dg-publish":true,"permalink":"/assets/templates/quest/","dgPassFrontmatter":true}
---

<%*
// ###########################################################
//                        Main Code Section
// ###########################################################

// Call modal form
const result = await MF.openForm('QUEST');

// Declare variables after form returns values
const name = result.Name.value;
const status = result.Status.value;
const location = result.Location.value;
const npc = result.Assignor.value;
const target = result.Assignee.value;

// Rename & open note
await tp.file.rename(name);
await app.workspace.getLeaf(true).openFile(tp.file.find_tfile(name));
new Notice().noticeEl.innerHTML = `<span style="color: green; font-weight: bold;">Finished!</span><br>New quest <span style="text-decoration: underline;">${name}</span> added`;
_%>

---
type: quest
target: <% target ? `"[[${target}]]"` : 'groupQuest' %>
locations:
- <% location ? `"[[${location}]]"` : ''  %>
tags:
- <% `quest/${status.toLowerCase()}` %>
headerLink: "[[<% name %>#<% name %>\|<% name %>#<% name %>]]"
---
###### <% name %>
<span class="sub2">:FasCircleExclamation: Quest &nbsp; | &nbsp; :FasListCheck: <% status %> <% npc ? `&nbsp; | &nbsp; :FasUser: [[${npc}#${npc}]]` : '' %></span>
___

> [!quote|no-t]
>ИЗОБРАЖЕНИЕ| ВСТАВЬ| СЮДА 
>ОПИСАНИЕ ПИШЕМ ТУТ

#### marker
> [!column|flex 3]
>>[!note]- История
>>```dataview
>>LIST WITHOUT ID headerLink
>>FROM "Сессионные Заметки" AND [[<% name %>\|<% name %>]]

