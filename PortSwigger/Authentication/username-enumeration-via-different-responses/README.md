# Username Enumeration via Different Responses

## Lab Information

- **Platform:** PortSwigger Web Security Academy
- **Category:** Authentication
- **Difficulty:** Apprentice
- **Tools Used:** Burp Suite Community Edition

---

## Objective

Identify a valid username by observing differences in the application's login responses.

---

## Background

Some web applications reveal whether a username exists by returning different responses during login attempts. An attacker can exploit these differences to enumerate valid usernames before attempting password attacks.

---

## Methodology

### Step 1: Intercept the Login Request

- Opened the login page.
- Entered test credentials.
- Intercepted the POST request using Burp Suite Proxy.
- Sent the request to Intruder.

### Step 2: Configure Intruder

- Attack type: Sniper
- Payload position: Username parameter
- Password: Kept constant
- Payload list: Username wordlist

### Step 3: Launch the Attack

Executed the Intruder attack and compared responses.

Observed:
- Response length
- Error messages
- Status codes
- Differences in response content

One username generated a different response, indicating that it was valid.

### Step 4: Complete the Lab

Used the valid username to continue the authentication process and successfully completed the lab.

---

## Why This Works

The application exposes information by responding differently for valid and invalid usernames. These subtle differences allow attackers to determine whether an account exists.

---

## Impact

- Username enumeration
- More efficient brute-force attacks
- Information disclosure

---

## Mitigation

- Return identical error messages.
- Keep response sizes consistent.
- Prevent timing differences.
- Implement rate limiting.
- Use account lockout and CAPTCHA where appropriate.

---

## Tools Used

- Burp Suite Proxy
- Burp Suite Intruder

---

## Skills Learned

- Burp Suite Proxy
- Burp Suite Intruder
- Authentication Testing
- Username Enumeration
- HTTP Request Analysis
