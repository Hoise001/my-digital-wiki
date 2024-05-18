```dataview
LIST WITHOUT ID headerLink
FROM "Компендиум/Атлас/<% location ? `${path}/` : '' %><% name %>"
WHERE type= "locale"
SORT file.name ASC
>
>> [!note]- История
>>```