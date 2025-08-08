- Before:
	- cannot edit full name and doesn't have the API
- After:
	- create an API to:
		- update the full name in Etiqa+ mongo DB
		- Update the full name in CDH through the CDH Integration App
		- do this in a single API
- Notes:
	- This ticket were meant for creating API for the Regional Backend to use. 
	- UI is not included
Figma:
- Registration: https://www.figma.com/design/3t91B570l9R0axpEkiAel3/Login---Register?node-id=1146-11297&t=EDrhHd2b8IKabn9X-4
- login: https://www.figma.com/design/3t91B570l9R0axpEkiAel3/Login---Register?node-id=1146-11306&t=EDrhHd2b8IKabn9X-4
- edit profile: https://www.figma.com/design/A9NicsZAFRu0gajbypwaLD/Edit-Profile?node-id=2002-13790&t=rYjAJ5CD4FyR4fjW-4

PR:

https://github.maybank.com/ETIQA-CHANNELS/smile-aio/pull/2907

ticket: https://jira.maybank.com.my/browse/ETQREGMOBA-955

Checklist
- [ ] Why new address added become the first one? (low prio)
- [ ] why are there userAddress and address (low prio)
- [ ] remove delete Button #urgent
	- [x] remove in edit page
	- [x] show in add page
- [x] remove additional add new data button #urgent 
- [x] check scenario when emptying input from address line 2 -> 5 in CDH API
	- [x] can it accept empty string? 
		- no. only null
	- [ ] should we sent null or empty string?
		- confirm with CK, Evonne. how is this going to be
- [x] remove log for request search party. too many