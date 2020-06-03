### Combined Reducers

```
import todoReducer from './todo.store.js';
import itemReducer from './item.store.js';

let reducers = combineReducers({
  todo: todoReducer,
  item: itemReducer,
});
```

- any component can reach into the store and get access

```
import * as actions from "../../store/todo.store.js";
import * as itemActions from "../../store/item.store.js";

const mapStateToProps = state => ({
  todo: state.todo,
  item: state.item,
});

const mapDispatchToProps = (dispatch, getState) => ({
  deleteItem: id => dispatch(actions.deleteItem(id)),
  hideDetails: id => dispatch(itemActions.hideDetails()),
});
```

- Obey the Single Responsibility Principle
- Each reducer really should have only 1 part of state to manage

```
// YES:
const initialState = { value: 0 };

// NO:
const initialState = { value: 0, numChanges:0, changes:[] };
```

- Each reducer has it’s own actions and creators.
- Activate multiple reducers

```
//counter.store.js
export default function reducer (state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { value: state.value + 1 }
    case 'RESET':
      return {value:0};
    default:
      return state;
  }
}

//history.store.js
export default function reducer (state = initialState, action) {
  switch (action.type) {
    case 'CLICK':
      return { clicks: state.clicks + 1 }
    case 'RESET':
      return {clicks:0};
    default:
      return state;
  }
}
```
