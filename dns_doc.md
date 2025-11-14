# DNS Configuration Documentation

## 1. Overview
This document explains how the domain **musf4rfits.site** was connected to the AWS EC2 server using GoDaddy DNS records.

---

## 2. Domain Provider
- **Registrar:** GoDaddy  
- **Domain:** musf4rfits.site  

---

## 3. DNS Records Configured

### 3.1 A Record (Root Domain)
This record links the domain directly to the EC2 public IPv4 address.

| Type | Name | Value (Points to) | TTL |
|------|------|-------------------|-----|
| A | @ | 13.48.55.181 | 1 hour |

This ensures visiting **musf4rfits.site** loads the website hosted on the EC2 instance.

---

### 3.2 CNAME Record (www Subdomain)
This redirects the “www” version of the domain to the root domain.

| Type | Name | Value (Points to) | TTL |
|------|------|-------------------|-----|
| CNAME | www | musf4rfits.site | 1 hour |

Now both:
- **musf4rfits.site**
- **www.musf4rfits.site**
point to the same server.

---

## 4. DNS Propagation
After updating DNS records:
Propagation can take ~30 minutes.
Verification can be done using:
```bash
ping musf4rfits.site
