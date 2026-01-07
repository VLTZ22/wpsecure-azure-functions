
# 🚀 Azure Functions used by WPSecure Personalization Packages

**WPSecure Personalization Packages**  
_(also known as **Windows Branding Packages**)_

WPSecure helps organizations centrally deploy and manage **branding and personalization** across Windows devices.

---

## 🎨 What Can Be Deployed?

WPSecure enables deployment of the following branding assets:

🖼️ **Desktop backgrounds**  
🔒 **Lock screen images**  
✉️ **Microsoft Outlook email signatures**  
🧑‍💼 **Microsoft Teams background images**  
🎬 **Video screensavers**

---

## 🔗 Helpful Links

🌐 **Product page:** https://wpsecure.shop/  
📘 **Documentation:** https://wpsecure.shop/documentation/

---

## 🏗️ Architecture Overview

✅ **Local‑first by design**

Once deployed, **nearly all WPSecure operations run locally on end‑user devices**, without reliance on:

- External infrastructure  
- Continuous internet connectivity  
- Third‑party service providers  

This ensures **privacy, performance, and reliability**.

---

## ☁️ When Is Azure Connectivity Required?

If an organization operates **exclusively on Microsoft Entra ID**  
(**no on‑premises Active Directory servers**), a small set of actions requires access to the Azure tenant.

---

## 🔑 Scenarios Requiring Azure Access

### 👤 1. User Attribute Retrieval
Used to dynamically generate **Outlook email signatures** by retrieving properties such as:

- First name  
- Surname  
- Email address  
- Mobile number  

---

### 📡 2. Beacon Engine Trigger
Triggers the **beacon engine** to collect and store user logon metadata in **SharePoint Online**, including:

- 🖥️ Device boot time  
- 🔑 User login time  
- 📊 Related sign‑in metadata  

This enables **reporting, auditing, and usage insights**.

---

### ✉️ 3. Exchange Online Signature Upload
Uploads and maintains the user’s **web-based email signature** in **Exchange Online**, ensuring consistency across:

- ✅ Outlook (New)  
- 🌐 Outlook on the Web (OWA)

---

## ⚙️ Azure Services Used

To support the scenarios above, WPSecure securely leverages:

🧩 **Azure API Management**  
⚡ **Azure Functions**

These services:

- Act as a secure integration layer  
- Run on scheduled or event‑driven triggers  
- Minimize cloud interaction to *only* what is required  

---

## 🛡️ Security & Design Philosophy

✅ **Minimal cloud dependency**  
✅ **No persistent external services**  
✅ **Native Microsoft 365 integration**  
✅ **Enterprise‑grade security posture**

---

