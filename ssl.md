# SSL/TLS (HTTPS) Documentation

## 1. Overview
This document explains how HTTPS encryption was configured for the website **musf4rfits.site** using **Let’s Encrypt Certbot** on an Apache2 web server hosted on AWS EC2.

---

## 2. Server Environment

| Component | Details |
|----------|---------|
| **Cloud Provider** | AWS EC2 |
| **Instance OS** | Ubuntu Server 22.04 LTS |
| **Web Server** | Apache2 |
| **Domain Registrar** | GoDaddy |
| **SSL Provider** | Let’s Encrypt |

---

## 3. Installing Certbot (SSL Tool)

First, update the server and install Certbot with Apache support.

bash
sudo apt update
sudo apt install certbot python3-certbot-apache -y

## 4. Generating and Installing the SSL Certificate
Run the following command:  
bash  
sudo certbot --apache  
During the interactive setup:  
  1. Certbot detects the domain configured in Apache
  2. You select the domain musf4rfits.site
  3. Certbot requests a certificate from Let's Encrypt
  4. Certbot installs the certificate into the Apache config
  5. Certbot asks whether to redirect all traffic to HTTPS

## 5. Automatic Certificate Renewal
Let’s Encrypt certificates are valid for 90 days, but Certbot automatically handles renewals.
To test automated renewal:
bash  
sudo certbot renew --dry-run  
Expected output:  
 Renewal successful  
 No errors detected  
Certbot installs a systemd timer that checks renewal twice per day.

## 8. Testing the SSL Certificate
8.1 Browser Check
Open: https://musf4rfits.site  
Verify:  
Secure padlock icon  
Certificate issued by Let’s Encrypt  
No browser warnings  
