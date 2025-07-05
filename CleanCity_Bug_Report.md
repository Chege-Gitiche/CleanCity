
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
