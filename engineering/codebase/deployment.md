# ☁ Deployment

Our apps are hosted at vercel.com, we use a custom `vercel-deploy.sh` deploy script in order to clone the monorepo, and the git submodules recursively.

### cal.com

The fastest way to deploy from `main`  to `production` is by force pushing (only admins can do that):

```
git push origin +main:production
```



### app.cal.com

### api.cal.com

### console.cal.com

