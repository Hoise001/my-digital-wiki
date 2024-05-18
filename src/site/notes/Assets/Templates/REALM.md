```dataview
LIST WITHOUT ID headerLink
FROM "Компендиум/Атлас/<% location ? `${path}/` : '' %><% name %>"
WHERE type= "continent" OR type="ocean"
SORT file.name ASC
>
>> [!note]- История
>>```