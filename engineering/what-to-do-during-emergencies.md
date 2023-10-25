# 🔥 What to do during Emergencies

{% embed url="https://media0.giphy.com/media/QMHoU66sBXqqLqYvGO/giphy.gif?cid=790b7611d6ef2df86bbca97e2e4410e27265a17d524f2ad7&ct=g&rid=giphy.gif" %}

We've recently experienced a DDoS attack, but an emergency can also be a faulty code change or unexpected downtime (Vercel, AWS, ...)

1. Keep a cool head
2. Gather as much information and open a thread titled: "\[Outage]: XYZ"
3. Research the Primary and Secondary Owners (see Areas of Expertise: [https://cal.com/open](https://cal.com/open))
4. If you are an owner, expect to drop whatever you are doing right now.
   * If you are working on an equally important ticket or are OOO, find another expert.
   * If you’re unsure of which task has more priority, contact **Bailey**, **Peer**, **Keith**, **Ciarán**
   * If you do not have access to prod and suspect it will be needed to resolve the issue, contact **Peer**, **Bailey**, **Keith**, **Zomars**, **Alex**, **Morgan** or **Erik** immediately.
5. Update the [cal.com-status-page.md](cal.com-status-page.md "mention") to inform users that we are investigating a reported outage and inform leadership, support and marketing teams to post on Twitter and Slack.
6. **Important: Our primary objective is to restore service to our users quickly.** Even before looking for root cause, ask yourself, "would a rollback to the previous version of Cal.com potentially fix this issue and not cause other problems?"
   * If rolling back seems like a legitimate option to restore service and there will not be other negative side effects (e.g. rolling back introduces other critical bugs that have been fixed) do the rollback and see if service is restored.
     * Example: A revert of [https://github.com/calcom/cal.com/pull/12019](https://github.com/calcom/cal.com/pull/12019) is what ultimately restored service for our booking page issues in negative UTC offset regions on October 23-24, 2023. Finding that this was the culprit was quite challenging due to other circumstances regarding idle DB connections and Cloudflare outages but it's a good reminder that by asking ourselves the question of "can we just rollback to the previous version" before trying to going deep to find the root cause, we might be able to bring service back to our users faster.
   * If a rollback is not a legitimate option, start to research root cause.
7. Once the root cause is found, update [cal.com-status-page.md](cal.com-status-page.md "mention") to inform users that we are currently working on a fix.
8. Keep the Threads thread up-to-date on all steps that have been taken, so other people know what to search for.
   * e.g. "Database not affected, just checked the logs"
   * e.g. "Vercel is reporting a downtime, see https://vercel-status.com"
   * e.g. "I can reproduce the issue locally, I am now rolling-back our last commit"
9. If you are approaching end-of-the-day and the problem is still ongoing, find a new owner and explain what steps you would've tried next.
10. Once service has been restored, update [cal.com-status-page.md](cal.com-status-page.md "mention") to inform users and update the Thread with the verification steps you took to ensure service was restored.
    * We need to see what was checked as part of giving the green light that everything is back to normal so that in the event everything is **not** actually back to normal or if the outage arises again, we'll be able to add further verification steps to ensure service is restored.
11. Keep a cool head. This too shall pass.
