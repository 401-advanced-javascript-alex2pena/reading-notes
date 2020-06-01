# `<Login /> and <Auth />`
*Authentication + Role Based Authorization*

What problems do we need to solve for?

- Is this a valid user (are they logged in)?
- What is the user authorized to do?
  - Which parts of our application care about this?
  - How can we determine this?
    - What’s in the token?
    - Contact between the UI and the API
- How do we make this easy to use?


### Proposal
`<Auth />` **component**

- Based on permissions it gives access to a component or jsx or hides it.
- Must not use Redux
  - Why? We don’t want to force implementors into a specific state management system.

```
// The div only shows if you are logged in
  <Auth>
    <div />
  </Auth>

// The div only shows if you are logged in AND have read permissions
  <Auth capability="read">
    <div />
  </Auth>
```
