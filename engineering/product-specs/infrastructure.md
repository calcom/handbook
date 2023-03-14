---
description: Everything there is to know about the Infrastructure Plan
---

# 🏢 Infrastructure

## Payments

* $189/month and first 500 bookings are free\\
* .05 cents for every additional booking (501 is $189/month + .05, 502 is $189/month + .10)
  * Every unique booking (rescheduled meetings for example) also get charged.&#x20;
* Customers will be charged at the end of the month (irrespective of usage) so even if a customer has not gone live yet, they will still be charged $189 at least

Example:

* Person A books with me (.05 cents)
* Person A reschedules (2 bookings now so .10 cents)
* Person A ends up canceling (still get charged .10 cents?)

## API

To get access to the API, a customer must first be invited by the team to signup at [console.cal.com](http://console.cal.com/). They must done complete the following steps:

1. Create a Deployment and add their credit card for the Infrastructure Plan
   1. There is no charge UNTIL they go live. Then the following applies:
   2. ![](<../../.gitbook/assets/CleanShot 2022-07-25 at 09.40.14@2x.png>)
2. Then customers are able to jump to Step 4 and request API Access
   1. Which opens up this Gmail message:
      1. ![](<../../.gitbook/assets/CleanShot 2022-07-25 at 09.43.41@2x.png>)
      2. Once they share their Github usernames, the email goes to team@cal.com and [Agusti Fernandez Pardo](https://app.gitbook.com/u/rohoKMreDNW1b1YQfzGAjB3P1Qi1 "mention")invites them to the repo in Github (adding collaborators)

## Self-Hosting FAQs

* Tech Stack Recommendation
  * &#x20;If using Vercel, we recommend using Amazon AWS RDS for the Postgres database.
  * Vercel is what we use for the frontend apps, but they can certainly self-host those too and self-deploy as a pm2 node regular app, or using docker/kubernetes, or whatever fits their needs.
  * For self-hosters that aren’t in needs to blitzscale, their probable best scenario is to have everything together (webapp, database, etc)
* Self-Hosting Pain Points
  * Some self hosters struggle with working around git submodules.&#x20;
  * We could let them know that they don’t need to, and can change their setup however they want, the thing is we have API (which they get invited to) and website/console (which they don’t and are only cal team).&#x20;
  * So then when they fork monorepo, they have those gitsubmodules failing.
  * They could just add api to their monorepo if ketp private. so they don’t need to deal with this (Submodules) and can keep their monorepo together.
* How to best prepare to self-host?
  * Their engineers should know how to deal with git submodules, if we provide them all the docs/info about it too in the README.
* Cal.com Tech Stack
  * NodeJS v16&#x20;
  * NextJS / Vercel for webapp / api deployments&#x20;
  * Postgres (Recommend Amazon’s AWS RDS if using vercel)
    * But we can work with them and help them deploy at any provider for sure, we already have some heroku/railsway app install
    * They can also use docker/docker-compose for deployment if they wish to. I think both heroku and railways apps work with the docker image. We’re working on integrating docker into monorepo in the future (soon enough) if possible. So using docker should be good too.

## **HIPAA**

Cal.com does not typically sign BAA (yet) and is only self-compliant when Self-Hosted which is typically only done through the Infrastructure Plan. Working towards having HIPAA on hosted, but no timeline.

