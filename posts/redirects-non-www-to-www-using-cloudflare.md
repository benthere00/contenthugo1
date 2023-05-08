---
title: "Redirect Non-WWW to WWW using Cloudflare as Clean Solution For Traefik: Step-by-Step Guide."
date: 2023-04-03T08:44:35Z
draft: false
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["cloudflare", "traefik", "redirection"]
categories: ["Web Server"]

lightgallery: true
---
---

You can find many instructions online on how to redirect from Non-WWW to WWW like Google search does. However, at the time of writing this, I couldn't find any that worked.  Particularly configuring Traefik as Proxy Server and Nginx as Web Server. 

<!--more-->

So, I came up with a solution to redirect using Cloudflare since they offer 3 free page redirection rules. It's a simple and effective way to do it, and you get the added benefit of using Cloudflare's services.

If you want to redirect non-www to www using Cloudflare, follow these step-by-step instructions:

1.  Log in to your Cloudflare account and select the domain you want to redirect.
2.  Click on the "Page Rules" tab.
3.  Click the "Create Page Rule" button.
4.  In the "If URL matches" field, enter your domain name without www, like example.com/*.
5.  Click the "Add a Setting" button and select "Forwarding URL".
6.  Choose "301 - Permanent Redirect" from the dropdown menu.
7.  In the "Destination URL" field, enter [https://www.example.com/$1](https://www.example.com/$1).
8.  Click "Save and Deploy".

By following these steps, all traffic to your domain without the www prefix will be automatically redirected to the www version.

I have done various things in both Traefik labels and its dynamic configurations, unfortunately I couldn't find any thing useful as I prefer to make our code maintainable.

It's important to note that a 301 redirect is a permanent redirect and it's preferred by search engines. By doing this, you're telling search engines that your website has permanently moved to the www version of your domain, which can help improve your search engine rankings.

That's it! Now all traffic to your domain without the www prefix will be automatically redirected to the www version.

Nice and clean right? Just comment below.
