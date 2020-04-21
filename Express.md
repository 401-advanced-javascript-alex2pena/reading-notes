# Express

### Express Routing

1. Event Driven
- `app.get('/thing', (req,res) => {})`
- This is the same pattern we see in Vanilla JS, jQuery
- ‘When a get event happens in our server, on “/thing”, run this function…’
2. Request Object
- (req,..)
- /:parameters
- `app.get('/api/:thing',...) = req.params.thing`
- Query strings
- `http://server/route?ball=round = req.query.ball`
3. Response Object
- `(..., res)`
- Responsible for sending data back to the browser
- Has methods like send() and status() that Express uses to format the output to the browser properly
- Sends headers
- Cookies
- Status codes

### Express Middleware

- Logging
- Dynamic Model Loading
- Browser, Location, User specific content
- Consistent Data Transition/Modeling/Preparation (Pre-Render)
- Each function receives request, response and next as parameters


1. Application middleware
- Error Handling
- Bringing in other routes
- Applies Defaults
- JSON, Body and Form Parsing
- Runs on every request

2. Route Middleware
- Dealing with specific things for a route
- Are you logged in?
- What is your IP?
- Have we seen you here before?

### Modularization & Separation of Concerns

- Modularizing your code into logical chunks
- Each thing should do the thing its best at

### CRUD Operations with REST and Express
- CREATE `app.post('/resource')`
- READ `app.get('/resource')`
- UPDATE `app.put('/resource/:id')`
- DESTROY `app.get('/resource/:id')`

### Server Testing
- Generally, avoid starting the actual server for testing. Instead, export your server as a module in a library
- Use supertest to run your tests, will hit your routes as though your server was running
- You test the data/veracity of the API when you write your API tests, not web server tests…

### Test Pyramid

??? 

