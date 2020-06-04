# Thunk
*Using Redux actions to connect to remote APIs via Thunk Middleware*

- Action generators return a function, like this:
```
const get = (payload) => {
  return {
    type: 'GET',
    payload: payload
  }
}
```
- Must perform asynchronous action before dispatching to reducer. 

- The action you dispatch from your React App returns a function, 
- Not an actual action object, which is what Redux expects and requires
```
let api = 'https://api.mockable.io/api/v1/stuff';

export const get = () => dispatch => {
  return utils.fetchData(api).then(records => {
    dispatch(getAction(records));
  });
};

const getAction = payload => {
  return {
    type: 'GET',
    payload: payload,
  };
};
```
- Implement redux middleware: “thunk” 
- Inspects every dispatched action 
- Then lets it go through || processes dispatches what the function returns.

- What does thunk middleware look like?
```
export default store => next => action =>
  typeof action === 'function'
    ? action(store.dispatch, store.getState)
    : next(action);
```
- Middleware is a curried function that evaluates the action
- Either:
  - Function gets invoked with the store’s dispatch() and getState() methods. 
  - (a normal action creator), it simply runs your action.
