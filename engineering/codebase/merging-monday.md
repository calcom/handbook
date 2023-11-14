# 🌝 Deploying to Production

We merge all reviewed and approved PR's to `main` and then merge to the `production` branch to start the automated deployment process.&#x20;

| Branch        | Deployed         | Envirorment |
| ------------- | ---------------- | ----------- |
| Pull Requests | \*cal.vercel.app | Preview     |
| main          | app.cal.dev      | Staging     |
| production    | app.cal.com      | Production  |

### Steps to release a new version

1. [Bump "version" in `apps/web/package.json` ](https://github.com/calcom/cal.com/edit/main/apps/web/package.json)according to semver standards, stage it in git and "Commit changes" directly to the `main` branch.\
   <img src="../../.gitbook/assets/image (6) (1).png" alt="" data-size="original"> ![](<../../.gitbook/assets/Screen Shot 2023-11-14 at 11.40.45 AM.png>)
2. Create a new release in GitHub:\
   [https://github.com/calcom/cal.com/releases/new](https://github.com/calcom/cal.com/releases/new)
3. Type the new version and hit "Create new tag: vX.Y.Z on publish"\
   ![](<../../.gitbook/assets/image (14).png>)
4. Use the "Create auto generated release text" button\
   ![](<../../.gitbook/assets/image (2) (1).png>)
5. Publish release\
   ![](<../../.gitbook/assets/image (11) (1).png>)
6. Profit!
