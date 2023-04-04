---
title: "Breach Threat! Someone Can Reveal Your Saved Password from the Browser"
date: 2023-04-03T11:57:40+08:00
lastmod: 2023-04-03T11:57:40+08:00
draft: false
author: "venven"
authorLink: "https://www.datacareph.com"
description: "Breach Threat! Someone Can Reveal Your Saved Password from the Browser"
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["data", "breach", "hack", "security"]
categories: ["Cyber Security"]

lightgallery: true
---

## Data can be Breach

We may be unaware of what’s really going on when we use our devices to access the internet. Well, this content will make you aware of what you should do when you use your favorite browser to access the internet. Hackers are eagerly pestering us to get our sensitive information, such as user credentials, passwords, credit card information, and the like.

Specifically, this information is limited to Mozilla Firefox and Google Chrome browsers, yet it may be similar to your favorite browser too.

The scenario (as an example) is that when you use your favorite web browser to login to your Facebook account, you’ll see something similar to this.!

![](facebook-uri.png "Facebook URI")
source: screenshot facebook login

From there, your browser prompts you to save the password or the website has a “Remember Password” checkbox field, so the issue starts from there. So the next question is, where do your login credentials go? How could you or someone else access it?

## Google Chrome Web Browser’s Password Autofill

When you access Facebook using the Chrome browser, just copy and paste the code below into your address bar and click the `eye icon` to reveal the password.

```
chrome://settings/passwords?search=manage
```

Autofill > Select specific login details
![[google-chrome-password-manager.png]]

In Chrome, when you click the eye icon, it prompts for admin privileges in order to see the password string, which is somewhat good news since it has a layer of authentication.

## Mozilla Firefox Web Browser’s Password Autofill

When you access Facebook using the Firefox browser, just copy and paste the code below into your address bar.

```
about:logins
```

And you’ll see something similar to this when you click on specific account, and click the `eye icon` to see the password naked.

![[mozilla-firefox-password-manager.png]]

## Other Browsers Too

Like I stated earlier, this is limited to Firefox and Chrome web browsers, but it may also occur in your favorite browser too.

## The Conclusion

Hence, allowing your web browser to save passwords for you is very risky and can be compromised, especially when you access the internet using a public computer. Google Chrome has a security layer as compared to Mozilla Firefox, for which it needs admin privileges, but believe me, it can still be bypassed.

## What to do then?

You may realize by now that we are susceptible to data breaches and prying hackers, though we still need web browser applications to access the internet. We can still access the internet with full precaution and awareness of what traces and sensitive information we might expose.

Here’s my recommendations and tips:

-   Just do not fully trust your web browser.
-   Do not put your trust in any unknown website.
-   Access the website only with `HTTPS` in the address bar in your browser like![[facebook-uri.png]]
-   Do not let the web browser save your password for you.
-   Access the Internet with full precaution with awareness of what information or traces you might leave especially sensitive information i.e. user login credentials, credit card info
-   I believe Google Password Manager is somewhat secure to let them remember passwords for you. i.e.

## My Final Thoughts

I wish popular browsers such as Google Chrome, Safari, and Mozilla Firefox would add more security layers such as hashing algorithms to keep passwords securely and remove the `show password` feature since I find it nonsense why it has to be there. As part of my roadmap, I’m going to keep publishing content on how we could somewhat securely access the Internet as part of data security information.

Please let me know your thoughts in the comment below.