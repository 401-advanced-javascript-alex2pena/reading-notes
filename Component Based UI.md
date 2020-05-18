# Component Based UI

- Classes and Functions are used to classify functionality
- Require what is needed 
- Render it where it is needed


```
JSX

const element = () => {
  return {
    <h1 className="greeting">
      Hello, world!
    </h1>
  }
);
```
Behind the scenes…
```

const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```
- [react hello world](https://facebook.github.io/react/docs/hello-world.html)
- [introducing JSX](https://facebook.github.io/react/docs/introducing-jsx.html)
- [rendering elements](https://facebook.github.io/react/docs/rendering-elements.html)
- [sass](https://sass-lang.com/)
- [sassmeister](http://www.sassmeister.com/)
- [sass cheatsheet](https://devhints.io/sass)
- [react cheatsheet](https://devhints.io/react)
- [another react cheatsheet](https://reactcheatsheet.com/)
