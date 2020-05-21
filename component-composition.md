# Component Composition

### Routing
- **react-router** can toggle the visibility of components and pages
- `import { Route } from 'react-router-dom'`
- Replace the <a> tags and use built-in <Link> component
```
<Link to="/">Home</Link>
<Link to="/stuff">Stuff</Link>
```
---
```
 <Route exact path="/" component={Home} />
 <Route exact path="/stuff" render={() => <List>{items}</List>} />
```
---
  
### Component Composition - Logical
- Used when sending your child components the raw data and allowing them to render the output


#### Dashboard Wrapper
- feeds the SearchForm some methods
- then feeds the results some data
```
<Dashboard>
  <SearchForm handler={this.doTheSearch} />
  <Results data={this.state.results} />
</Dashboard>
```
#### Results Component
```
<ul>
  {this.props.data.map( (item,i) => <li key={i}>{item}</li> );
</ul>
```
### Component Composition - Using Logic-less Children
- Used when your children are already in JSX form (pre-rendered) and you need to display them as a whole. 
- *(ie) a gallery of images*
```
<Dashboard>
  render() {
    let listings = {this.state.results.map( (item,i) => <li key={i}>{item}</li> );
  }
  <SearchForm handler={this.doTheSearch} />
  <Results>
    { listings.map( listing => listing ) }
  </Results>
</Dashboard>
```
#### Results Component
```
<ul>
  {this.props.children}
</ul>
```
