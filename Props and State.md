# Props and State
---

### Forms and Inputs
- React form elements maintain internal state. 
- Think of React inputs as stateful child components. 
- Must manage the state of inputs through our own stateful component and one way data binding. 
- The creation of a parent component manages the state for all child components through the use of props. 
- Each input has an onChange event that we can *handle* each time the user interacts with an input.

### Props
- Components accept arbitrary inputs called props. 
- In JSX, props are passed into a component with a syntax that looks like HTML.
- Props is the name of the object passed into a component constructor.
- After props they are available on the context by using **`this.props`**.
- Props can be data or functions

---
```
Props Example … the way we get to use them
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
Props – what’s actually happening under the hood

const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```
---

#### When this renders …

- Foo will draw Bar
- Bar will draw a button
- When that button gets clicked, it’s onClick action fires
- That action runs the method this.props.handleClick
- That method runs in <Foo> … <Foo> passed it down to <Bar> essentially telling it what it wants it to do.
- This is a means of passing not only Data but Behavior down the component tree

---
```
class Foo extends React.Component {
  constructor(props){
    super(props)
  }

  screamLoud() {
    console.log("OUCH");
  }

  render(){
    return (
      <div>
        <Bar handleClick={this.screamLoud} />
      </div>
    )
  }
}

class Bar extends React.Component {

  constructor(props) {
    super(props);
  }

  render() {
    <div>
      <button onClick={this.props.handleClick}>Click</button>
    </div>
  }

}

// Render the element ...
<Foo />
```
---

### One Way Data flow
- State can only be passed from parent component to a child component through the use of props. 
- This enforces the idea of one way data flow. 
- State can only be passed down the component tree (not up). 
- If a child wants to pass some data to a parent:
  - The parent can pass a function to the child through props
  - The child may invoke that function and pass it data to the parent.
