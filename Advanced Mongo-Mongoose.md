# Advanced Mongo/Mongoose
*Testing Node.js + Mongoose with an in-memory database*
[Link to code on GitHub](https://github.com/pawap90/test-mongoose-inmemory)

### Pro's
- No need for mocks
- Faster development cycle
- More reliable (tests actual code)
- Tests are easier to build

### Con's
- The in-memory database probably needs seeding
- More memory usage (dah)
- Tests take longer to run (depending on your hardware).

## Setup & Install dependencies
- npm install --save mongoose
- npm install --save-dev jest mongodb-memory-server

## Write code to test
- 
