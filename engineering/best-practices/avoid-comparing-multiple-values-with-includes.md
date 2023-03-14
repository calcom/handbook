# Avoid comparing multiple values with \`includes\`

Instead of doing:

```typescript
if (req.method === "POST" || req.method === "PUT" || req.method === "DELETE") {
  console.log("Method allowed");
}
```

Do:

```typescript
if (["POST", "PUT", "DELETE"].includes(req.method)) {
  console.log("Method allowed");
}
```

This will very situational, but when comparing multiple values you can use include to improve legibility. Also make sure that an [early return isn't more appropriate first](avoid-comparing-multiple-values-with-includes.md#prefer-early-returns).
