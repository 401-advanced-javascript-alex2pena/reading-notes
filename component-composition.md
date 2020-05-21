Readings: Component Composition
Below you will find some reading material, code samples, and some additional resources that support today’s topic and the upcoming lecture.

Review the Submission Instructions for guidance on completing and submitting this assignment.

Reading
Routing
Using react-router, you can easily toggle the visibility of components (or even pages) based on the URL/Route that the user engages with.

import { Route } from 'react-router-dom';

To use Browser Router properly, you eliminate your use of <a> tags and instead use it’s built-in <Link> component.

<Link to="/">Home</Link>
<Link to="/stuff">Stuff</Link>
In practice, then, use the router component to look at either / or /stuff and based on that, displaying either the Home or the List component…

 <Route exact path="/" component={Home} />
 <Route exact path="/stuff" render={() => <List>{items}</List>} />
Component Composition - Logical
In this setup, you are sending your child components the raw data and allowing them to render the output as they decide.


// Dashboard Wrapper
//  - feeds the SearchForm some methods
//  - then feeds the results some data

<Dashboard>
  <SearchForm handler={this.doTheSearch} />
  <Results data={this.state.results} />
</Dashboard>

// .. Results Component
<ul>
  {this.props.data.map( (item,i) => <li key={i}>{item}</li> );
</ul>

Component Composition - Using Logic-less Children
This is typically used when your children are already in JSX form (pre-rendered) and you need to display them as a whole. A good example might be a gallery of images

<Dashboard>
  render() {
    let listings = {this.state.results.map( (item,i) => <li key={i}>{item}</li> );
  }
  <SearchForm handler={this.doTheSearch} />
  <Results>
    { listings.map( listing => listing ) }
  </Results>
</Dashboard>

// Results Component

<ul>
  {this.props.children}
</ul>
