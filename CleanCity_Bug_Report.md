
# 🐞 CleanCity Security & Bug Report

This report highlights major security vulnerabilities and functional bugs discovered during testing of the CleanCity Waste Pickup Scheduler web application.

---

## 🔐 Security Vulnerabilities

### 1. Plaintext Password Storage
- **Issue:** User passwords are stored in localStorage as plain text.
- **Risk:** High — susceptible to theft via browser inspection or XSS attacks.
- **Location:** `dataService.addUser()` and login logic.

---

### 2. No Authorization Checks
- **Issue:** Any user can update or delete any user profile.
- **Risk:** Medium to High — allows account tampering.
- **Location:** `dataService.updateUser()` and `dataService.deleteUser()`.

---

### 3. Insecure Session Management
- **Issue:** Session data is stored in localStorage with no expiration or protection.
- **Risk:** High — sessions can be hijacked or persist indefinitely.
- **Location:** `dataService.getCurrentUser()`

---

### 4. Vulnerable to IDOR
- **Issue:** Users can access others’ data via ID-based functions without restriction.
- **Risk:** High — privacy violation and data leakage.
- **Location:** `getUserById(userId)`, `getUserByEmail(email)`

---

### 5. Input Validation Weakness
- **Issue:** Password and name validations are weak; email validation is minimal.
- **Risk:** Medium — allows low-quality or harmful data.
- **Examples:**
  - Password accepts only 3 characters
  - Name accepts 2 characters
  - Email uses basic `includes("@")` check

---

## 🧪 Functional Bugs

### 6. Location Filter Bug
- **Issue:** Filtering pickup requests by "Eldoret" shows results from "Nairobi".
- **Impact:** Incorrect data display.
- **Location:** `filterRequestsByLocation(location)` function.

---

### 7. Feedback Form — Missing Required Validation
- **Issue:** Feedback comment field is not validated.
- **Impact:** Users can submit empty feedback.
- **Location:** `validateFeedbackForm()`

---

### 8. Pickup Request Date — Not Enforced
- **Issue:** Preferred date is optional even though scheduling depends on it.
- **Impact:** May create unusable pickup requests.
- **Location:** `validatePickupForm()`

---
### 9. Invalid Email Format Accepted
**Summary:**  
Website accepts invalid email format: `user@com`

**Description:**  
During registration testing, the system incorrectly accepts the email `user@com`, which lacks a valid domain suffix (e.g., `.com`, `.org`). This bypasses standard email validation rules.

**Environment:**  
- **Browser:**  Microsoft Edge 

**Severity:** Minor  
**Priority:** Medium  

**Steps to Reproduce:**
1. Go to the registration page  
2. Enter name and password fields with valid values  
3. Enter email as `user@com`  
4. Submit the form  

**Expected vs Actual:**
- **Expected:** The system should display an error like “Invalid email format” and prevent submission.  
- **Actual:** The system accepts the email and proceeds with registration.

**Attachments:**
![Alt text describing the image](bug_images/email.png)

### 10. Weak Password Policy Enforced
**Summary:**  
Password policy too weak — accepts passwords with only 3 characters and no complexity requirements

**Description:**  
The system allows users to register with passwords as short as 3 characters and doesn't enforce complexity rules (no numbers, symbols, or uppercase letters required). This is a major security risk and encourages poor password practices.

**Environment:**  
- **Browser:** Microsoft Edge  

**Severity:** Major  
**Priority:** High  

**Steps to Reproduce:**
1. Navigate to the registration page  
2. Enter a valid name and email  
3. Enter password as `abc` or `123`  
4. Confirm password  
5. Submit the form  

**Expected vs Actual:**
- **Expected:** Password should be rejected if it’s too short or lacks required complexity.  
- **Actual:** Passwords like `abc` or `123` are accepted.

**Attachments:**
![Alt text describing the image](bug_images/password.png)

## ✅ Confirmed Fixes by Jest Tests
- XSS input is sanitized
- Weak passwords rejected
- Email format validated
- Empty comments blocked
- Name length enforced

---

## 📌 Recommendation
- Fix all critical security issues
- Improve validation across all user input
- Implement basic role-based access checks for user actions

---

**Tested by:** QA Analyst  
**Test Tool:** Jest + Manual Code Review  
**Date:** July 2025
