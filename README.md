# Task 2 - Identify phishing characteristics in a suspicious email sample

Phishing is a type of cyberattack where attackers impersonate legitimate organizations or individuals to trick people into revealing sensitive information—such as passwords, credit card numbers, or login credentials—usually through fake emails, messages, or websites.

Goal is to steal data, gain unauthorized access, or install malware.
Common signs: Suspicious links, urgent language, spoofed email addresses, and poor grammar.

---

## Sample Phishing Email (Fake PayPal Notification)

> **Subject:** Account Notice: Immediate Action Required
>
> **From:** "PayPal" <[support@paypalsecurity-alert.com](mailto:support@paypalsecurity-alert.com)>
>
> **Body:**
> Dear Customer,
>
> We have detected unusual activity in your account. To protect your account, access has been temporarily limited.
>
> Please confirm your identity immediately to avoid permanent suspension:
> [Click here to verify your account](http://paypal-security-verification.com/login)
>
> Failure to act within 24 hours will result in account termination.
>
> Thank you for choosing PayPal.
>
> * PayPal Security Team

---

## Step-by-Step Analysis

### 1. **Sender's Email Address**

* `support@paypalsecurity-alert.com` — clearly **not** an official PayPal domain (`paypal.com`).
* **Spoofing Attempt Detected.**

### 2. **Email Headers**

* Analyze headers using [MxToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx).
* Look for:

  * **Return-Path** mismatch
  * **SPF**, **DKIM**, or **DMARC** failures
  * IP address of sending server not matching PayPal
* Likely shows **forged domain** and **misleading reply-to address**.

### 3. **Suspicious Links or Attachments**

* Link goes to: `http://paypal-security-verification.com/login`
* Not a legitimate PayPal site.
* Uses **HTTP** instead of **HTTPS** (no encryption).
* Phishing attempt to steal credentials.

### 4. **Urgent or Threatening Language**

* “**Immediate Action Required**”
* “**Failure to act will result in account termination**”
* Fear tactics are a **classic phishing hallmark**.

### 5. **Mismatched URLs**

* Hovering shows the actual link (`paypal-security-verification.com`) differs from what the user expects (`paypal.com`).
* **Deceptive Link Detected.**

### 6. **Spelling or Grammar Errors**

* In email: Possibly no errors in this sample, but many phishing emails **do** contain grammar mistakes like:

  * “Thank you for choosing PayPal.” (Overly formal / robotic tone)
  * Sometimes poor punctuation or missing personalization.

---

## Summery

| Trait                            | Evidence                                                                    |
| -------------------------------- | --------------------------------------------------------------------------- |
| **Fake Sender Address**          | [support@paypalsecurity-alert.com](mailto:support@paypalsecurity-alert.com) |
| **Header Discrepancies**         | Likely forged headers with failed SPF/DKIM                                  |
| **Suspicious Link**              | Leads to fake domain using HTTP                                             |
| **Urgent Language**              | "Immediate Action Required", "account termination"                          |
| **Mismatched URL**               | Displayed vs actual URL mismatch                                            |
| **Possible Grammar/Tone Issues** | Generic, impersonal phrasing                                                |

---
