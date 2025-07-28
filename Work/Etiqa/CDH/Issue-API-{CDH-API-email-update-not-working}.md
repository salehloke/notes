
Email update / add not working:
- emails is always not being added
- this is the body request
- then, its always send id=null
- when sending id=null it means, not created yet in cdh
- when update to cdh, its not being added
- sync into eplus, the process repeat


```json {

"party": {

"partyTypeCode": "PI",

"identifiers": [

{

"idTypeCode": "001",

"idValue": "771106015506",

"ecif": "PIMYS25073EPPEY39F4"

}

],

"name": {

"fullName": "Cdh Test Bin thirty one",

"nickname": null

},

"contacts": [

{

"id": null,

"contactTypeCode": "M",

"countryDialingCode": "+60",

"phoneNumber": "0132050031",

"primaryIndicator": true,

"verifiedIndicator": true

},

{

"id": 800,

"contactTypeCode": "M",

"countryDialingCode": "+63",

"phoneNumber": "9228356944",

"primaryIndicator": false,

"verifiedIndicator": false

},

{

"id": 797,

"contactTypeCode": "M",

"countryDialingCode": "+63",

"phoneNumber": "9176523348",

"primaryIndicator": false,

"verifiedIndicator": false

},

{

"id": 798,

"contactTypeCode": "M",

"countryDialingCode": "+63",

"phoneNumber": "9954728234",

"primaryIndicator": false,

"verifiedIndicator": false

},

{

"id": 801,

"contactTypeCode": "M",

"countryDialingCode": "+63",

"phoneNumber": "9175747975",

"primaryIndicator": false,

"verifiedIndicator": false

},

{

"id": 799,

"contactTypeCode": "M",

"countryDialingCode": "+63",

"phoneNumber": "9616495897",

"primaryIndicator": false,

"verifiedIndicator": false

}

],

"emails": [

{

"id": null,

"emailTypeCode": "1",

"emailAddress": "7711060155226@email.com",

"primaryIndicator": true,

"verifiedIndicator": true

},

{

"id": 663,

"emailTypeCode": "1",

"emailAddress": "edelsuyo@gmail.com",

"primaryIndicator": false,

"verifiedIndicator": true

},

{

"id": 660,

"emailTypeCode": "1",

"emailAddress": "mylene.inigo23@gmail.com",

"primaryIndicator": false,

"verifiedIndicator": true

},

{

"id": 661,

"emailTypeCode": "1",

"emailAddress": "iampaulineroxas@gmail.com",

"primaryIndicator": false,

"verifiedIndicator": true

},

{

"id": 664,

"emailTypeCode": "1",

"emailAddress": "geoffpineda@gmail.com",

"primaryIndicator": false,

"verifiedIndicator": false

},

{

"id": 662,

"emailTypeCode": "1",

"emailAddress": "lombreswshh@gmail.com",

"primaryIndicator": false,

"verifiedIndicator": false

}

],

"addresses": [

{

"id": null,

"addressTypeCode": "Home",

"line1": "2223",

"line2": null,

"line3": null,

"line4": null,

"line5": null,

"postalCode": "82100",

"city": "Ayer Baloi",

"stateCode": "JHR",

"countryCode": "MYS",

"primaryIndicator": true,

"verifiedIndicator": false

}

]

}

}
```