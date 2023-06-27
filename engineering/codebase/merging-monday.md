# 🌝 Merging (Monday)

We merge all reviewed and approved PR's automatically to main, but then on monday we will cherry-pick from main and deploy to `production` branch. This ensures we have time to catch any bugs or missing stuff during the whole week at staging (cal.dev)

| Branch         | Deployed         | Envirorment |
| -------------- | ---------------- | ----------- |
| main           | app.cal.dev      | Staging     |
| production     | app.cal.com      | Production  |
| Pull Request's | \*cal.vercel.app | Preview     |

### Step-by-step to release a new version

1. [Bump "version" in `apps/web/package.json` ](https://github.com/calcom/cal.com/edit/main/apps/web/package.json)according to semver standards and stage it in git and "Commit changes"\
   <img src="../../.gitbook/assets/image (6) (1).png" alt="" data-size="original"> <img src="../../.gitbook/assets/image (8).png" alt="" data-size="original">
2. Create a new release in GitHub:\
   [https://github.com/calcom/cal.com/releases/new](https://github.com/calcom/cal.com/releases/new)
3. Type the new version and hit "Create new tag: vX.Y.Z on publish"\
   ![](<../../.gitbook/assets/image (14).png>)
4. Use the "Create auto generated release text" button\
   ![](<../../.gitbook/assets/image (2) (1).png>)
5. Publish release\
   ![](<../../.gitbook/assets/image (11) (1).png>)
6. Profit!
