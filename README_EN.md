# README_EN.md - Phishing Simulation Framework

## 1. Introduction

The **Phishing Simulation Framework** project is designed to simulate a complete phishing attack in a controlled lab environment. Its primary goal is to help learners understand how modern phishing attacks operate, from crafting malicious emails to capturing user credentials and session data.

Instead of focusing only on theory, this project implements the full attack workflow in practice, allowing direct observation of both system behavior and user interaction.

> (Image - System architecture overview)

---

## 2. Project Objectives

The project aims to achieve the following:

* Simulate real-world phishing attack workflows
* Understand how phishing emails are created and delivered
* Analyze user behavior when interacting with phishing emails
* Collect and evaluate campaign data
* Study credential harvesting techniques
* Understand session hijacking and 2FA bypass mechanisms

---

## 3. System Architecture

The system follows a client-server model and consists of the following components:

### 3.1 Attacker Server

This is the core component of the system, responsible for:

* Running **GoPhish** to create and manage phishing campaigns
* Running **Evilginx2** to perform Man-in-the-Middle attacks
* Collecting victim data (credentials and sessions)
* Storing and analyzing collected data

### 3.2 SMTP Server

* Used to send phishing emails to target users
* Can be configured using services like Mailgun, Gmail SMTP, or a custom mail server

### 3.3 Phishing Domain

* A fake domain configured to resemble legitimate websites
* Helps increase credibility and deceive users

### 3.4 Victim (Target User)

* Receives phishing emails
* Interacts with malicious links
* May unknowingly provide sensitive information

### 3.5 Logging System

* Records all campaign activities, including:

  * Email opens
  * Link clicks
  * Credential submissions
  * Session cookies

> (Image - Detailed system architecture diagram)

---

## 4. Technologies Used

Main technologies and tools used in this project:

* **GoPhish** – phishing campaign management and tracking
* **Evilginx2** – reverse proxy for MITM and session hijacking
* **Ubuntu Server** – deployment environment
* **SMTP Server** – email delivery (Mailgun / Gmail / custom SMTP)
* **HTML/CSS/JavaScript** – phishing landing pages

---

## 5. System Workflow

The phishing simulation follows these steps:

### Step 1: Campaign Setup

* Create email templates (phishing content)
* Design fake landing pages
* Configure phishing domain
* Set up campaign in GoPhish

> (Image - GoPhish campaign setup interface)

### Step 2: Email Delivery

* Send phishing emails via SMTP server
* Emails contain links to fake websites

> (Image - Sample phishing email)

### Step 3: User Interaction

* User clicks the link in the email
* Request is routed through Evilginx (reverse proxy)
* Evilginx forwards traffic to the legitimate website

> (Image - Request flow through Evilginx)

### Step 4: Data Collection

When users enter their credentials:

* Username and password are captured
* Session cookies are intercepted

> (Image - Captured credentials log)

### Step 5: Data Analysis

After the campaign, the system provides insights such as:

* Email open rate
* Click-through rate
* Credential submission rate
* Collected credential data

> (Image - GoPhish dashboard statistics)

---

## 6. Key Techniques

### 6.1 Phishing Emails

* Mimic legitimate communications
* Use urgency and psychological triggers

### 6.2 Fake Landing Pages

* Clone real websites
* Maintain a familiar user experience

### 6.3 Man-in-the-Middle (MITM)

* Evilginx acts as a reverse proxy
* Intercepts communication between user and real server

### 6.4 Credential Harvesting

* Captures login credentials entered by users

### 6.5 Session Hijacking

* Extracts session cookies after authentication
* Allows account access without password or 2FA

> (Image - MITM and session hijacking illustration)

---

## 7. Results

After implementation, the system achieved:

* Successful deployment of a phishing simulation framework
* Execution of phishing campaigns
* Collection of real interaction data
* Better understanding of:

  * Phishing techniques
  * Credential harvesting
  * Session hijacking

---

## 8. Limitations

* Operates only in a controlled lab environment
* Depends on domain and SMTP configuration
* Some security systems may detect and block phishing attempts
* Does not fully replicate real-world attack complexity

---

## 9. Conclusion

This project provides a comprehensive and practical simulation of modern phishing attacks. By implementing the full workflow, learners can gain deeper insights into how these attacks function and improve their ability to detect and defend against them in real-world scenarios.

> (Image - Full system demo)
