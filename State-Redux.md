# Application State with Redux


- Requires the combination of 3 distinct aspects into a “Store” 
- All components can have access to the "store"

### State
- Reducers - (strategies to alter state)
- Actions (methods that get “dispatched” or “run”, which trigger associated reducers)

### Redux Store ###
- Where your application state is stored. 
- It's job is to identify the various reducers. 
- Middleware used globally.
- React uses “reducers” to hold and manage state. 
- Reducers manage just one part of the larger application state.
- It creates an initial “empty” state
- Then identifies what todo when called. 
- Reducers hear the "dispatch", and “payload”

```
let initialState = { customerId: null, items: [] };

const myReducer = (state = initialState, action) => {
  let { type, payload } = action;

  switch (type) {
    case 'INITIALIZE':
      return {customerId: payload.id};

    case 'ADD_ITEM':
      return { items: [...items, payload.item] };

    case 'CLEAR':
      return initialState;

    default:
      return state;
  }
};
```

React applications with Redux dispatch “actions” (like an event) with “payload” (data). 
An action creator function as shown below always returns an action object with the action type to perform and the data to perform it with. 
When your component wants to modify state, it “Dispatches” (calls) an action and sends whatever payload (data) 
it needs to, to the reducer.

When an action is dispatched, a reducer responds to it, and receives that payload, where it then operates on state using it.

```
// actions.js
const newCart = customer => {
  return {
    type: 'INITIALIZE',
    payload: customer,
  };
};
```

We use a **store** to “bring it all together” 

```
import { createStore, combineReducers, applyMiddleware } from 'redux';

import cartReducer from './reducers/cart.js';

let reducers = combineReducers({
  cart: cartReducer,
});

export default () => createStore(reducers);
```

- Components subscribe to the store code

*In this example:* 
- when the ‘Start Shopping’ button is clicked
- it runs a method called this.props.initializeTheCart().
- This method is declared in the mapDispatchToProps function as a pointer to the newCart() method in the actions file.

```
import React from 'react';
import { connect } from 'react-redux';

import * as actions from '../store/actions.js';

class App extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <button onClick={this.props.initializeTheCart}>
        Start Shopping!
      </button>
    );
  }
}

const mapStateToProps = state => ({
  cart: state.cart,
});

const mapDispatchToProps = (dispatch, getState) => ({
  initializeTheCart: () => dispatch(actions.newCart()),
});

export default connect(
  mapStateToProps,
  mapDispatchToProps,
)(App);
```

- Before any of this can work, your entire application needs to be given access to the store. 
- Your component (above) uses the redux connect() method to attach to the store, 
- The provider wrapper allows child components to have access to parents.

```
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';

import './style.scss';

import App from './components/app';

import createStore from './store';
const store = createStore();

class Main extends React.Component {
  render() {
    return (
      <Provider store={store}>
        <React.Fragment>
          <App />
        </React.Fragment>
      </Provider>
    );
  }
}

const rootElement = document.getElementById('root');
ReactDOM.render(<Main />, rootElement);
```
