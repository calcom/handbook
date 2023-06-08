---
description: As part of our monorepo, we have some private git submodules that are private.
---

# 🚫 Git Private Submodules

### Why?

Although we try to keep as much of our codebase as possible open source. We don't want to make it too easy for a wanna be competitor or copy-cat to just clone our repo and setup mycal.com to compete with us, thus, some more sensitive parts of our codebase or like our landing / marketing pages at cal.com will remain private closed source repos, which will live under git private submodules in our main monorepo.

### Website

This is our main landing page when you go at cal.com, it contains our proprietary signup implementation, which let's you purchase a subscription for a -premium- username at cal.

It also contains our blogposts and other landing pages.



### Console

The console is a private repo and not shared with anyone, console is where we control all the related stuff to deployments, keys, add-ons, etc. All kind of users will access it via console.cal.com to manage their subscriptions/deployments/keys for self-hosted enterprise instances.

Since we don't want any code related to console to leak into the public repos, it syncs with the user at website when you signup, but creates a new user in a separate console database that holds the customer data. This user data gets synced via cronjob once a day.



### API

Although API is a private submodule and closed-source, self-hosted infra customers can get access to the code in order to run API alongside their self-hosted cal instance.
