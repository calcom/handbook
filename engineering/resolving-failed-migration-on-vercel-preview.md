# 🔺 Resolving failed migration on Vercel Preview

We currently use a single DB for all preview deployments corresponding to various branches. (There is on going work to have different DB per branch. This approach would still remain applicable as repeat deployments of same branch would fail.)

Sometimes, a faulty migration in one of those in progress branches, can fail which can start failing all builds of other branches as well.

![A sample failure on Vercel build.](<../.gitbook/assets/Screenshot 2022-07-15 at 10.41.55 AM.png>)

#### Steps to fix the issue

* Get the name of the failed migration(e.g. in the above case it is _20220714175322\_destination\_calendar\_one\_to\_many\_bookings_)
* Go to **prisma** folder in the repo. Modify DATABASE\_URL temporarily to Preview DB. You can get the credentials from Vercel Environment Variables(Preview). _It might be a good idea to have that variable remain there as commented, so that you can easily switch_
* Once, you have ensured that, DATABASE\_URL is updated, run following command from prisma folder `yarn prisma migrate resolve --rolled-back 20220714175322_destination_calendar_one_to_many_bookings`. This should fix the rollback the failed migration ensuring all other branches deploy fine.
* Note that the branch having the issue should fix the migration problem to avoid this issue from coming again and again.&#x20;
