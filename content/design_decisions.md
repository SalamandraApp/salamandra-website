---
title: "Design Decision"
---

# Why we don't use identity providers

Identity providers (eg. login with Google, Facebook...) often lack open-source practices, making it difficult to trust privacy measures. 
We're not comfortable relying solely on size and reputation of a company when it comes to user data. 

## Secure Password Management

We use and recommend [KeePassDX](https://www.keepassdx.com/#download) for Android and [KeePassXC](https://keepassxc.org/) for Desktop.

Instead of using the same password for everything you can generate a secure password and store the encrypted password database guarded under the **only** master password you need to remember.

![](/images/keepass.png)
