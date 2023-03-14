---
description: >-
  In this example the constant isn't really being used anywhere else, so it
  doesn't add any benefit to abstract to a constant in the first place.
---

# Prefer inferred types over explicit ones

Instead of doing:

```typescript
const teamInviteEvent: TeamInvite = {
  language: t,
  from: session.user.name,
  to: usernameOrEmail,
  teamName: team.name,
  joinLink: BASE_URL + "/settings/teams",
};

await sendTeamInviteEmail(teamInviteEvent);
```

Do:

```typescript
await sendTeamInviteEmail({
  language: t,
  from: session.user.name,
  to: usernameOrEmail,
  teamName: team.name,
  joinLink: BASE_URL + "/settings/teams",
});
```
