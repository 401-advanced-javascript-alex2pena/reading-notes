# Custom Hooks

- What are custom hooks?
  - Extract duplicated logic from components
  - Share common functionality
    - Except for state…
  - Take advantage of useEffect lifecycle
- Common use cases – make things DRY!
  - Handle forms easily
  - Pre-fetch API data
  - Connect to services (like socket.io, Q, etc)
- A custom Hook doesn’t need to have a specific signature. 
- We can decide what it takes as argument & what it should return. 

A simple example that demonstrates proper wiring.

- Hooks are exported as a function, named as useXXX()
- Hooks return data or behaviors (functions) that are required to reuse their internal functionality
- Hooks are imported into components
- Components can re-use the hook functionality or data/state as needed
- Hooks do not render


**use-food-hook.js**

```
export default function useFoodHook(hungry) {
  let food = 'cookies';
  return hungry ? food : null;
}
Using a hook is a simple, then, as requiring it and calling it.

my-component.js

import useFeedme from 'use-food-hook.js';
function myComponent() {
  const food = useFeedMe(true);
  return <div>{food}</div>
}
```
