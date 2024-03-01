---
title: "Design Decision"
---

# Why we don't use identity providers

Identity providers (eg. login with Google, Facebook...) often lack open-source practices, making it difficult to trust their security, but mostly privacy measures. 
We're not comfortable relying solely on size and reputation of a company when it comes to sensitive user data. 
Also, using identity providers centralizes logins, ending up with all you accounts under you Google/Apple/Facebook/Amazon. 

## Secure Password Management

We use and recommend [KeePassDX](https://www.keepassdx.com/#download) for Android and [KeePassXC](https://keepassxc.org/) for Desktop.

You can generate a secure password and store the encrypted password database guarded under the only master password you need to remember.

![](/images/keepass.png)
