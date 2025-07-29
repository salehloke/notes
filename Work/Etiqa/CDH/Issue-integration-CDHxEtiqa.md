

| Issue                                   | status                           | Scope              | Root cause                                                                                             | solution                                                                                     | remarks                                                      |
| --------------------------------------- | -------------------------------- | ------------------ | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| Cannot add email with submit-party api  |                                  | CDH-api            | N/A                                                                                                    | reach out to CDH Dev team                                                                    |                                                              |
| cannot update and sync to CDH           | -[ ]  done    pending deploy uat | Backoffice         | operation using ic no instead of userId                                                                | use User ID for unique value. non unique value will cause sync issue because of missing data | [[Issue-API-{CDH-API-email-update-not-working}]]             |
| duplicate primary values                | done. pending to deploy uat      | backoffice-api<br> | - merging data from cdh into etiqa+. both have its primary values<br>- this occurs in syncCdhIntoEplus | - data from etiqa+ will always becomes primary                                               | - set etiqa+ as main db. so, it will be always replacing the |
| Cannot update backend operation         |                                  | backend-api        | operation using ic no instead of userId                                                                | use User ID for unique value. non unique value will cause sync issue because of missing data |                                                              |
| value for updateCdh is still in swagger |                                  |                    |                                                                                                        |                                                                                              |                                                              |


## Scripts

okay before we start with the POST API, iwant to tell you how we should these api. these are additional knowledge and info i want you to follow.  
  
1. after you do the api call (POST PUT OR PATCH OR ANY OPERATION), then u need to check the value in etiqa+ db.  
2. the api to check data in etiqa+ is :  
curl -X 'GET' \ 'http://localhost:10100/api/v5/mobile-cdh/sync-cdh-into-eplus/68872f804dba512547573d41' \ -H 'accept: application/json'  
  
3. from the result, obtain the idNo, then proceed on calling CDH API to check if the value is being reflected. :  
curl -X 'POST' \ 'http://localhost:10100/api/v5/mobile-cdh/retrieve-details-direct-cdh/no-logs' \ -H 'accept: */*' \ -H 'Content-Type: application/json' \ -d '{ "client": { "idType": "001", "idValue": "771106015507", "ecif": "" } }'  
4. the response from retrieving details from cdh is:  
  
{ "data": { "type": "https://tools.ietf.org/html/rfc7231#section-6.3.1", "title": "OK", "status": 200, "instance": "/api/parties/search", "success": true, "traceId": "00-9738d0ae4d0744b81bc26f83270b16e3-79dc3706773fa181-01", "data": { "partyTypeCode": "PI", "ecif": "PIMYS2507U6ORJ2F7F0", "titleCode": null, "birthDate": null, "birthCountryCode": null, "genderCode": null, "maritalStatusCode": null, "religionCode": null, "raceCode": null, "nationalityCode": null, "monthlyIncome": null, "currencyCode": null, "fundSourceCode": null, "smokerIndicator": false, "identifiers": [ { "idTypeCode": "001", "idValue": "771106015507" } ], "name": { "fullName": "CdhTest bin thrity two", "firstName": null, "middleName": null, "lastName": null, "nickname": null }, "preferences": { "contactMethodCode": null, "languageCode": null }, "employments": [], "addresses": [ { "addressTypeCode": "Home", "line1": "2211", "line2": null, "line3": null, "line4": null, "line5": null, "postalCode": "54070", "city": "Brickfields", "stateCode": "KUL", "countryCode": "MYS", "primaryIndicator": true, "id": 843 } ], "contacts": [ { "contactTypeCode": "M", "countryDialingCode": "+60", "phoneNumber": "0017200032", "verifiedIndicator": true, "primaryIndicator": true, "id": 1043 } ], "emails": [ { "emailTypeCode": "1", "emailAddress": "cdhTest32@email.com", "verifiedIndicator": true, "primaryIndicator": true, "id": 876 } ], "bankAccounts": [] }, "timestamp": "2025-07-29T01:31:39.1802659+08:00" } }  
5. then from the response in step 2, i want you to check, if the email / contact / address is being set as primary, it will replace the user.email , user.phoneNo, user.CountryCode. and user.address. do these five steps first, step by step, and document each step before we proceed.
6. Then, check if the email is checked as verify, and the email is the primary, update the value of the user.isEmailVerified.
7. Then, check if the primary phone number checked as verified, check the user.isPhoneNoVerified
8. compare value from cdh and etiqa. preferably create a table to compare value of emails, addresses, contacts and also fullName.
9. the expected outcome of this test is to expect that the value from these actions will sync accross these 2 db.

checklist:
- Perform API operation (POST/PUT/PATCH) for test case
- Check value in etiqa+ DB using GET API
- Obtain idNo and call CDH API to retrieve details
- Compare data between etiqa+ and CDH (primary & verified status, values)
- If primary/verified, ensure user fields are updated accordingly
- Document each step and create comparison table
- Confirm values sync across both databases