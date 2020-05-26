# Hooks
*React hooks allow to to easily create and manage state in a functional component.

- Hooks must be named with a use prefix (i.e. useFishingPole)
- Only call Hooks at the top level. 
- Don’t call Hooks inside loops, conditions, or nested functions.
- Only call Hooks from React function components. 
- Don’t call Hooks from regular JavaScript functions. 

### Built In Hooks

**useState()**
- Returns a stateVariable and setterFunction for you to use to manage state
```
 function Counter() {
   const [clicks, setClicks] = useState(0);

   return (
     <div>
       <h2>Button has been clicked {clicks} time(s)</h2>
       <button type="button" onClick={() => setClicks(clicks + 1)}>
         Update Count
       </button>
     </div>
   );
 }

 export default Counter;
 ```
