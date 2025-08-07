
## Verification Checklist

- [ ] Primary email updates user.email
	- so that it won't impact the existing user
	- this happens on the backend, can use the user data modal to check
- [ ] Primary contact updates user.phoneNo and user.countryCode 
	- so that it won't impact the existing user
	- this happens on the backend, can use the user data modal to check
- [ ] Primary address updates user.address
	- so that it won't impact the existing user and have similar patter to the other new cdh input
- [ ] Verification status properly updates user.isPhoneNoVerified and user.isEmailVerified
	- so that it won't impact the existing user 

- [ ] Only one primary item exists in each category
- [ ] All updates from Etiqa+ are synchronized with CDH
	- Comparison modal has been created to ease tester, and the rest of the team to cross check data

- [ ] All data from CDH is correctly reflected in Etiqa+
	- This mainly cover Full name, Contacts, addresses and emails during this phase (as per mentioned By CK)
	- use cdh comparison modal created by saleh to check this
- [ ] address must be optional
	- due to the current etiqa+ user doesn't have this fields

- [ ] must be able to register without any address
- [ ] must be able to edit profile without address
- [ ] scenario to test

## 