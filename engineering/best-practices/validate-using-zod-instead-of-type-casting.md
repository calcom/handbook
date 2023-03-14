---
description: >-
  Whenever we are parsing unknown json where we know the shape the object should
  have but it is not typed from source, it is worth the extra effort to use zod
  so we get both type and runtime safety.
---

# Validate using zod instead of type casting

Instead of doing:

```typescript
type DeploymentCreateBody = {
  deploymentName: string,
  deploymentType: "CLOUD" | "SELFHOSTED",
}

const { deploymentName, deploymentType } = req.body as DeploymentCreateBody;
```

Do:

```typescript
const deploymentCreateSchema = z.object({
  deploymentName: z.string().min(1),
  deploymentType: z.nativeEnum(DeploymentType),
});

const { deploymentName, deploymentType } = deploymentCreateSchema.parse(req.body);
```
