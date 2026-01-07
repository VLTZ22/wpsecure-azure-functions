
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
(**no on‑premises Active Directory servers**), A small set of actions requires access to the Azure tenant.

---


# 🔐 WPSecure Architecture Overview

WPSecure leverages **Azure API Management (APIM)** and **Azure Functions** to deliver a secure, scalable, and automated platform for managing Outlook web signatures, retrieving user attributes non-interactively for all Outlook signatures, and collecting system and user telemetry when they login to their device.

The solution is designed to operate **non-interactively**, to securely access Microsoft Graph, Exchange Online, and SharePoint Online without disrupting the end-user experience.

---

## 🧩 Core Components

### 🔹 Azure API Management (APIM)

APIM serves as the centralized and secure gateway for all WPSecure service interactions. It provides:

- mTLS Certificate-based authentication with complete certificate chain verification.
- Request validation and throttling  
- Centralized logging, monitoring, and auditability  
- Controlled exposure of backend Azure Functions
- IP filtering  

All external and internal calls to WPSecure services are routed through APIM, ensuring consistent security and governance.

---

### 🔹 Azure Functions

Azure Functions host the backend logic that interacts with Exchange Online, Entra ID, and SharePoint. These functions operate behind APIM and are invoked securely as needed.

---

## ✉️ Outlook Signature Management

WPSecure uses Azure Functions to silently retrieve user attributes from **Microsoft Entra ID** via **Microsoft Graph**, including:

- Display name  
- Job title  
- Department  
- Phone numbers and contact details
- and other attributes

These attributes are used to generate and update email signatures dynamically for the following Outlook clients.

- **Outlook on the web**
- **Outlook Classic**
- **Outlook New**

This ensures consistent, centrally managed signatures across all Outlook clients and user devices.

---

## 👤 Non-Interactive Outlook web signature uploads to Exchange Online

Whenever the Outlook signature changes or every 8 hours, WPSecure sends a copy of the user's web signature to Exchange Online via the Azure Function.

---

## 💻 System and Device Telemetry Collection

Azure Functions also collect key operational and endpoint signals, such as:

- User login activity  
- System boot time  
- Device and session-related metadata  

This information is written to **SharePoint**, providing a centralized location for:

- Reporting and analytics  
- Auditing and compliance  
- Operational monitoring and insights  

---

## ✅ Summary

By combining **Azure API Management** and **Azure Functions**, WPSecure delivers an automated, secure, and centrally governed solution for:

- Outlook Web, New and Classic signature management  
- Non-interactive retrieval of user identity attributes  
- System and device telemetry collection into SharePoint  

---

