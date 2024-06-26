---
{"dg-home":false,"dg-publish":true,"permalink":"/assets/templates/note/","dgPassFrontmatter":true}
---

<%*
// ###########################################################
//                        Helper Functions
// ###########################################################

// Get next session note number
function nextNumber() {
  const sessionRegex = /^Session Notes\/Session (\d+)/;
  const files = this.app.vault.getMarkdownFiles()
    .reduce((maxNumber, file) => Math.max(maxNumber, (file.path.match(sessionRegex) || [])[1] || 0), 0) + 1;
  
  return files < 10 ? '0' + files : files.toString();
}

// ###########################################################
//                        Main Code Section
// ###########################################################

// Call modal form
const result = await MF.openForm('NOTE');

// Declare variables after form returns values
const date = result.Date.value;
const title = result.Title.value;
const location = result.Location.value.length ? result.Location.value.map(value => `- "[[${value}]]"`).join("\n") : '- ';
const number = nextNumber();
const name = `Session ${number} (${date})`;

// Rename & open note
await tp.file.rename(name);
await app.workspace.getLeaf(true).openFile(tp.file.find_tfile(name));
new Notice().noticeEl.innerHTML = `<span style="color: green; font-weight: bold;">Finished!</span><br>New session note added`;
_%>

---
type: notes
locations:
<% location %>
tags:
- 
headerLink: "[[<% name %>#<% title %>\|<% name %>]]"
---

![session.png|banner](/img/user/Assets/Images/session.png)
###### <% title %>
<span class="sub2">:FasSun: День 00 &nbsp; </span>
___

> [!quote|no-t] Подробности
>Recap of the session's events here.

#### marker
> [!column|flex 3]
>> [!info|felx] НПСы:
>> - [[Characters\|Characters]] (status)
>
>> [!example|flex] Локации:
>> - [[Locations\|Locations]] (status)
>
>> [!important|flex] Квесты:
>> - [[Quests\|Quests]] (status)
