# Component Based UI

Classes and Functions are used to classify functionality
Require what is needed 
Render it where it is needed


```
JSX

const element = () => {
  return {
    <h1 className="greeting">
      Hello, world!
    </h1>
  }
);
Behind the scenes…

const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```
