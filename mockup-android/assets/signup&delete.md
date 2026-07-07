---
visibility: hidden
---

# Sign-Up Flow Documentation
This document outlines the steps involved in the sign-up flow for our application.**

## Sign-Up Flow 

|SrN.| Steps | Description                             | Screen                               | 
|----|--------|-----------------------------------------|--------------------------------------|
| 1 | User clicks on the "Sign Up" button|For unauthorized users. The "Sign Up" button is prominently displayed.|<img src="/mockup-andriod/assets/signup.png" width=200> |
| 2 | <ol><li>Enter **phone number/Email ID**</li><li> Clicking on submit</li>| Navigates to the OTP screen & verify| <img src="/mockup-andriod/assets/emailid1.png" width=200> |
| 3 | User enters correct OTP received on email id or phone number and clicks on **verify** button| After verification, User navigates on patient main screen  | <img src="/mockup-andriod/assets/otp.png" width=200>|
| 4 |If the user enters an invalid OTP| User  gets the error message will be "Invalid OTP"| <img src="/mockup-andriod/assets/invalidotp.png" width=200>|


## Profile-Delete Module

|SrN.| Steps | Description                             | Screen                               | 
|----|--------|-----------------------------------------|--------------------------------------|
| 1 | User clicks on Profile | Following details displayed - Name, Role, Phone No., App verison & **Delete account** | <img src="/mockup-andriod/assets/Profile delete option.png" width=200> |
| 2 | After clicking on the **Delete account**| A confirmation dialog box appears| <img src="/mockup-andriod/assets/deletedialog.png" width=200> |
| 3 | Click on Delete account in the confirmation box| User navigates to the OTP screen for deletions.|<img src="/mockup-andriod/assets/delete account.png" width=200> |


## Logic , Errors & Validations 
1. If the user enters an invalid phone number or email address, the error message will be `"Enter a valid phone number or email address."`
2. If the user enters an invalid OTP , the error message will be `"Invalid OTP"`.
3. If the user enters the OTP after the time limit is over, the error message will state `"OTP expired"`.
4. `"Too many attempts. Please try after 5 min"` when the user enter after 5 mins .
5. Users receive a **snack bar** when an unauthorized user accesses the app with their account.
6. After filling the username and clinic name, User navigates to the Patient Landing screens.
7. Form validation is crucial here to ensure data integrity.






