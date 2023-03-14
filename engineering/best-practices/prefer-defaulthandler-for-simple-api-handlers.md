# Prefer defaultHandler for simple API handlers

Instead of checking for each method:

```typescript
export default async function handler(req: NextApiRequest, res: NextApiResponse) {
   if (req.method === "GET") {
    res.status(202).json({ message: "getting something" });
  }
  if (req.method === "POST") {
    res.status(202).json({ message: "posting something" });
  }
  if (req.method === "PATCH") {
    res.status(202).json({ message: "patching something" });
  }
}
```

Prefer splitting each method logic in their own files and use `defaultHandler` to auto-handle missing methods. And keep legibility when checking for individual method logic.

```typescript
// _get.ts
import { defaultResponder } from "@calcom/lib/server";

async function getHandler(req: NextApiRequest, res: NextApiResponse) {
  req.statusCode = 200;
  return { message: "getting something" };
}

export default defaultResponder(getHandler);


// _post.ts
import { defaultResponder } from "@calcom/lib/server";

async function postHandler(req: NextApiRequest, res: NextApiResponse) {
  req.statusCode = 200;
  return { message: "posting something" };
}

export default defaultResponder(postHandler);


// _patch.ts
import { defaultResponder } from "@calcom/lib/server";

async function patchHandler(req: NextApiRequest, res: NextApiResponse) {
  req.statusCode = 200;
  return { message: "patching something" };
}

export default defaultResponder(patchHandler);


// index.ts
import { defaultHandler } from "@calcom/lib/server";

export default defaultHandler({
  GET: import("./_get"),
  POST: import("./_post"),
  PATCH: import("./_patch"),
});
```

{% hint style="info" %}
If you have only one method, splitting in files may be overkill. Instead you can keep all in one file but still benefit from auto-method handling by doing the following to comply with the TS signature.
{% endhint %}

```typescript
import { defaultHandler, defaultResponder } from "@calcom/lib/server";

async function getHandler(req: NextApiRequest, res: NextApiResponse) {
  req.statusCode = 200;
  return { message: "getting something" };
}

export default defaultHandler({
  GET: Promise.resolve({ default: getHandler }),
});
```
