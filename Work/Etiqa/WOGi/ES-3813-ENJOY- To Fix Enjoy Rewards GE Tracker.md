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
          tapFrom: 'Explore Icon'
          errorMessage: '',
}
itemDetails: {
          etiqaExpiryDate: "DDMMYY",
          wogiExpiryDate: "DDMMYY"          
}

```

### login_ontap_enjoy_useDealNow
-  apply The New Tracking Format:
```
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
          tapFrom: 'Explore Icon'
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
	- [ ] 