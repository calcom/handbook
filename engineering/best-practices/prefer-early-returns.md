---
description: >-
  It is recommend to throw/return early so we can ensure null-checks and prevent
  further nesting.
---

# Prefer early returns

Instead of doing:

```typescript
function handler(req, res) {
  const session = await getSession({ req });
  if (session) {
    const user = getUserFromSession(session)
    
    if (user) {
      return res.status(200).json({ user });
    }
    return res.status(404).json({ message: "No user found" });
  }

  res.status(401).json({ message: "Not authenticated" });
}
```

Do:

```typescript
function handler(req, res) {
  const session = await getSession({ req });
  if (!session) return res.status(401).json({ message: "Not authenticated" });
  
  const user = getUserFromSession(session)
    
  if (!user) return res.status(404).json({ message: "No user found" });

  return res.status(200).json({ user });
}
```

It is recommend to throw/return early so we can ensure null-checks and prevent further nesting.

{% embed url="https://www.youtube.com/shorts/JnFh2NoAM4s?feature=share" %}
