# 💻 How we work on Tickets

### Linear and SyncLinear.com

We use [linear.app](https://linear.app) for all issue tracking and use [synclinear.com](https://synclinear.com), our self-made Linear 🔄 GitHub Sync tool to 1-to-1 sync tickets.

> This app lets you mirror Linear tickets to public GitHub issues, comments and all. This way, open-source teams can chat with contributors without giving access to an internal Linear team.

By default, every ticket from Linear will be sent to GitHub and comments and statuses will be synced back and forth.

Non-team members such as open-source contributors can continue to create tickets on [Github](https://github.com/calcom/cal.com/issues) and Cal.com Core members can assign the label "linear" to sync it back into Linear.

The roadmap will continue to be public: [cal.com/roadmap](https://cal.com/roadmap).

We run on a monthly tagged release schedule with multiple minor releases each week.

When you're joining the team, make sure to join the "Cal.com, Inc." Linear team and then visit [synclinear.com](https://synclinear.com)

* click "Connect to Linear" and make sure to select the “Engineering team” on the Linear dropdown and not “Product team”
* click "Connect to GitHub" and select calcom/cal.com

## Process for taking on work

**It's extremely important all engineers follow this process. Otherwise, keeping milestones up to date with the latest and greatest prioritized work is almost impossible.**

* Source of truth: [Priority engineering view](https://linear.app/calcom/view/b58fd0a4-3637-4980-b26a-5a4a3fd2e8ec) in Linear
  * For tracking milestones, we use Linear Projects (v3.5, v3.6, etc.). This view will be automatically filtered based on our current milestone.
    * **Project** in Linear lines up to the **Milestone** in GitHub (for now because cycles in Linear don't work well for lining up the dates)
  * This is what will always be kept up to date by the Product team. **Do not start work on something unless it's listed here.** If you think something needs to be taken on and it's not yet in this view, contact the Product team.
  * We should take work from the top down in terms of priority. It should be rare you find yourself taking on work that has lower priority than other issues with higher priority that have not yet been started. If you don't feel comfortable starting an issue with higher priority for whatever reason, contact someone from the **Product** team.
* If any items are marked as **Urgent**, drop what you are doing and pick up the issue.
  * Assign yourself and change its status to **In Progress.**
  * If an **Urgent** item is already assigned but no marked as **In Progress**, contact that person and check on the status. If it's actually not in progress, take it. If it is in progress, mark it as **In Progress** in Linear.
* If there are no **Urgent** items, take an item you are comfortable working on from the **next highest item in the list.**&#x20;
  * Note: This list can be manually prioritized, which will be handled by the Product team. **Do not move items around.**

## Linear Tips and Tricks

### Use Favorites to reduce noise

![](<../.gitbook/assets/CleanShot 2022-10-12 at 20.47.42@2x.png>)

### Use Keyboard shortcuts

* Hover over a function to see the keyboard shortcut

### Add mobile website to Homescreen for PWA experience

* on iPhone, open linear.app on Safari and "Add to Homescreen"
* on Android, open with Chrome and "Add to Homescreen"

### Add "linear" to Github tickets from Community members

* They'll then show up and sync in Linear

### Remove "Public" label for private issues

* For sensitive issues in Linear (such as userdata or security issues), remove the "Public" label

### Raycast App: [https://www.raycast.com/raycast/linear](https://www.raycast.com/raycast/linear)

<figure><img src="../.gitbook/assets/CleanShot 2022-10-13 at 10.38.32@2x.png" alt=""><figcaption></figcaption></figure>

## **Linear** Issue vs Discussion

Our [Issues](https://github.com/calcom/cal.com/issues) should only include **code-related issues.**

{% embed url="https://www.loom.com/share/1a632ac5341f4a1cb0182fb45cabdd76?t=3" %}
