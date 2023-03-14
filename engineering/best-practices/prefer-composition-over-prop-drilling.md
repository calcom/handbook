# Prefer Composition over Prop Drilling

Instead of relying on prop drilling, let's try to take advantage of react children feature. Having this as an example:

{% code overflow="wrap" lineNumbers="true" %}
```typescript
import React from "react";
import { Profile } from "./profile";

function Header({ loggedIn, handleSetLoggedIn }) {
  return (
    <>
      <Profile loggedIn={loggedIn} handleSetLoggedIn={handleSetLoggedIn} />
    </>
  );
}

function App() {
  const [loggedIn, setLoggedIn] = React.useState(false);

  const handleSetLoggedIn = () => {
    setLoggedIn(!loggedIn);
  };

  return <Header loggedIn={loggedIn} handleSetLoggedIn={handleSetLoggedIn} />;
}
```
{% endcode %}

Instead of "drilling props" all the way down, focus having everything as top level as possible:

```typescript
import React from "react";
import { Profile } from "./profile";

function Header({ children }) {
  return (
    <>
      {children}
    </>
  );
}

function App() {
  const [loggedIn, setLoggedIn] = React.useState(false);

  const handleSetLoggedIn = () => {
    setLoggedIn(!loggedIn);
  };

  return (
    <Header>
      <Profile loggedIn={loggedIn} handleSetLoggedIn={handleSetLoggedIn} />
    </Header>
  );
}
```

### More sources on this topic

* [Composition: An Alternative to Props Drilling in React](https://javascript.plainenglish.io/composition-in-react-f02afe24bc46)
* [A better way of solving prop drilling in React apps](https://blog.logrocket.com/solving-prop-drilling-react-apps/)
* [Strategies for mitigating prop drilling with React and TypeScript](https://blog.logrocket.com/mitigating-prop-drilling-with-react-and-typescript/)
