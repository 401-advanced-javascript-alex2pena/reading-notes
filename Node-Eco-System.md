# File naming rules
- be consistant
- case matters(use lower)
- use kabob casing "i-am-sentance"
- forcing a file or making it important (use uppercase)

# Node.js
- Open source framework
- V8 javascript runtime
- v8 was developed for chrome
- uses an event loop to run asyncronous I/O with ease

# Package.json
- Only requires **Name** & **Version**
- Use `npm init` or `npm init -y` to create
- seperate dependencies (`devDependencies`&`dependencies`

# semantic versioning
- known as **semver**
- **semver** formats the version number using a `MAJOR.MINOR.PATCH` construct
- MAJOR version when you make incompatible API changes
- MINOR version when you add functionality in a backwards-compatible manner,
- PATCH version when you make backwards-compatible bug fixes.

# CommonJS modules
- Organize code into smaller files
- makes scaling easier
- Use `module.exports` & `require` to join files

# Test Driven Development
- A methodology for writing code
- Speds up development cycle
- Validates integrity of new code
- Helps developers understand their goals

## 3 steps of TDD
- Red - make a plan, then write test for expected behavior
- Green - Write draft code to pass test
- Recaftor - Refactor code for speed & memory optimization

# Running Tests

- Install `jest` and `eslint` as dependencies
- Install a valid .eslintrc.json file in your project
- Edit your package.json to include test commands (see below)
- Run `npm test` in your project to run your test suite
- Run `npm run test-watch` in your project to continually test your code as you develop.

# Continous Integration

- Process of regularly merging individual features
- Can automate static analysis, running tests, testing platform support, enforce code reviews....

# Continous Delivery

- Developing software in short cycles
- With CI helps mainatin a constant working code base

# GitHub Actions

- a hosted and distributed continuous integration service
- used to build and test software projects
- Uses a `.yml` file in a folder `.github/workspaces`
- Once setup it will run tests with every push/pull
