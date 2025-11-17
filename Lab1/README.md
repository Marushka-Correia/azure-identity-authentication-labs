## This lab simulates a situation where a user who is unable to sign in due to issues related to MFA, authentication methods,
## or Conditional Access, and troubleshoot the problem using Azure tools — the same workflow used by Microsoft Technical Support Engineers.


## Step 1 — Create a Test User

Go to Azure Portal → Microsoft Entra ID
 - Select Users
 - Click New user → Create new user

Fill:
Username: testuser
Name: Test User
Password: Create manually

Click Create

## Step 2 — Enable MFA for the User

Go to Microsoft Entra ID → Users
 - Select Test User
 - Click Authentication methods
 - Toggle Require multifactor authentication → ON

## Step 3 — Simulate a Login Failure

Open a private browser window
 - Log in as the test user
 - Do not complete MFA or intentionally misconfigure it to cause a failure
 - Observe the error message displayed
 - ## This replicates a typical support case such as “My account is stuck at MFA.”

Step 4 — Investigate Using Sign-In Logs

In Azure Portal, open Microsoft Entra ID
 - Go to Sign-in logs
 - Filter by User: Test User
 - Open the failed login attempt

   ## Check the following fields:
   Status: Failure
   Failure reason
   Conditional Access → Result
   Authentication Details (whether MFA was requested or failed)

This is the core troubleshooting skill Microsoft expects.

Step 5 — Identify the Root Cause

Common causes you may find:
- User has no registered MFA method
- MFA is required by Security Defaults
- Conditional Access enforced MFA but user not registered

User account status is blocked

Risk-based policy triggered

Step 6 — Apply the Fix
Fix  — Re-register MFA
 User → Authentication methods
 Remove existing methods
 Click Require re-register MFA


Step 7 — Verify Resolution
 Attempt sign-in again as the test user


You should now be able to log in successfully
Review sign-in logs to confirm:
Status: Success

MFA: Satisfied

Conditional Access: Not blocking
