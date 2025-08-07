https://jira.maybank.com.my/browse/ES-3813

REference:
	https://docs.google.com/spreadsheets/d/1Y6LgAhabelmj7tUl9N6F1wqyEA3ZVKfGgRjMi_Q8IHI/edit?usp=sharing 

### login_ontap_enjoy_claimVoucher
- The new Tracking data format
```JSON
category: 'Login',
eventName: 'login_ontap_enjoy_claimVoucher',
trackingType: '',
module: 'Enjoy',
eventDetails: {
          timestamp: new Date(),
          deviceId: deviceId ?? '',
          session: '',
          appVersion: appVersion,
          deviceType: phoneOs,
          osVersion: phoneOsVersion,
          screenName: screenName,
          clickTarget: clickTarget,
          tapFrom: 'Explore Icon',
          errorMessage: '',
}
itemDetails: {
          etiqaExpiryDate: "DDMMYY",
          wogiExpiryDate: "DDMMYY"          
}

```
### API to call:
```Http
POST http://localhost:10100/api/v5/tracking/on-tap

Content-Type: application/json

Authorization: Key mobile.OHhZjK7cRZcKvjw2JS1EdoDJOldBuAOk6ILnK1IcIehSoS8NDmh

  

{

"category": "Login",

"eventName": "login_ontap_enjoy_claim_voucher",

"trackingType": "onTap",

"module": "Enjoy",

"screenName": "voucher-details",

"tapFrom": "Explore Icon",

"clickTarget": "",

"deviceId": "test-device-123",

"appVersion": "1.0.0",

"phoneModel": "iPhone 14",

"phoneOs": "iOS",

"phoneOsVersion": "16.0",

"session": "test-session-123",

"itemDetails": {

"voucherId": "VOUCHER_123",

"voucherName": "Test Voucher",

"brandName": "Test Brand",

"etiqaExpiryDate": "2025-01-01",

"voucherExpiryDate": "2025-02-02"

}

}
```


### login_ontap_enjoy_useDealNow
-  apply The New Tracking Format:
```JSON 
category: 'Login',
eventName: 'login_ontap_enjoy_useDealNow',
trackingType: '',
module: 'Enjoy',
eventDetails: {
          timestamp: new Date(),
          deviceId: deviceId ?? '',
          session: '',
          appVersion: appVersion,
          deviceType: phoneOs,
          osVersion: phoneOsVersion,
          screenName: screenName,
          clickTarget: clickTarget,
          tapFrom: 'Explore Icon',
          errorMessage: '',
}
itemDetails: {
          voucherName: "xxxxyyyzzz"    
}
```

- Update the Tracker
	- [ ] Test for the current value applied in the tracker
	- [ ] Check the new Value want to apply:
	- [ ] Reference for the

claim: 
4896. upon success

```json
{
  "data": {
    "productId": 9340,
    "transactionReferenceNumber": "68906bfbff72925644ec4d66",
    "status": "claimed"
  }
}
```




## 