---
description: >-
  We use turborepo to manage our calcom monorepo, which contains all our code,
  both public open source (calcom, etc) and private closed source (website, api,
  console)
---

# 🏎 Monorepo / Turborepo

You might already be familiar with monorepos with lerna and yarn workspaces, but we also uso turborepo to cache as much as possible the deployment of our monorepo.

[https://turborepo.org/](https://turborepo.org/)

Turbo repo builds pipelines see `turbo.json` so you can require any packages in other `apps` or `packages`

\
As you can see too, instead of having all code under packages, turborepo makes the apps distinction for apps that are inteneded to be deployed as full apps. This is mainly a nomenclature thing but helps differentiate them.

### &#x20;apps

&#x20;Apps are intended to be deployed at vercel.com as full-fledged webapps, and are usually nextjs based in our case.

### Our apps

* apps/web - main webapp that lives under app.cal.com
* apps/website - our landing and marketing site at cal.com
* apps/api - our Public API deployed at api.cal.com
* apps/swagger - our API auto-generated OpenAPI Spect
* apps/docs

#### Publish in your app an empty folder for deployment, make use of .gitkeep

{% hint style="info" %}
When deploying an app, you will need to have an empty folder inside:

`/apps/{yourappname}/apps/{yourappname}/.gitkeep`

This is necessary in order for the cloning of the monorepo and submodules, and then deployment of your app, to work properly as orchestrated from the `scripts/vercel-deploy.sh` in your app.
{% endhint %}



### packages

When you're requiring a local package from the monorepo, like `@calcom/ui` (unlike one from npm) like `react`, you just need to provide it's name and an asterisk for version, in the `package.json` this will make it available when you transpile it if you require it, for example in your next.config.js with the plugin transpile-modules withTM()

This allows you to require local packages from our monorepo in your own package or app, so there's no need to wrangle versions, releases and publishing to npm, since those packages are not to be consumed by 3rd party apps and only necessary for us there's no need to publish them. Some of the packages might be published on their own, like embed or sdk.

