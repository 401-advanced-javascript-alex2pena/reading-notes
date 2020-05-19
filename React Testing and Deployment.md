# React Testing

- Snapshots - Make assertions on the exact rendered markup (with content) at any state of the application.
- Render Testing - Similar to snapshots, but allows for jQuery-like inspection of the virtual DOM tree
- Shallow Testing - Executes and renders the called/container component, but does not compose children.
- Mounting - Executes the full component and children. Allows for inspection of rendered Virtual DOM & current state
---
**Sample** 
```
import React from 'react';
import renderer from 'react-test-renderer';
import Counter from '../../../../src/components/counter/counter.js';

describe('<Counter/> (Enzyme Test)', () => {
  it('is alive at application start', () => {
    let app = mount(<Counter />);
    expect(app.find('.count').text()).toBe('0');
  });

  it('can count up', () => {
    let app = mount(<Counter />);
    app.find('.up').simulate('click');
    expect(app.state('count')).toEqual(1);
    app.find('.up').simulate('click');
    expect(app.state('count')).toEqual(2);
  });

  it('can count down', () => {
    let app = mount(<Counter />);
    app.find('.down').simulate('click');
    expect(app.state('count')).toEqual(-1);
    app.find('.down').simulate('click');
    expect(app.state('count')).toEqual(-2);
  });

  it('visually displays proper polarity and value on the count element', () => {
    let app = mount(<Counter />);
    expect(app.find('.count.negative').exists()).toBeFalsy();
    expect(app.find('.count.positive').exists()).toBeFalsy();
    // Go to 1
    app.find('.up').simulate('click');
    expect(app.find('.count.positive').exists()).toBeTruthy();
    expect(app.find('.count').text()).toBe('1');

    // Down to zero
    app.find('.down').simulate('click');
    expect(app.find('.count').text()).toBe('0');
    expect(app.find('.count.negative').exists()).toBeFalsy();
    expect(app.find('.count.positive').exists()).toBeFalsy();

    // Down to -1
    app.find('.down').simulate('click');
    expect(app.find('.count.negative').exists()).toBeTruthy();
    expect(app.find('.count').text()).toBe('-1');
  });
});

describe('<Counter/> Core Component (Snapshot Test)', () => {
  it('renders right', () => {
    const component = renderer.create(<Counter />);
    let tree = component.toJSON();
    expect(tree).toMatchSnapshot();
  });
});
```
---
### Deployment
- Reacts development mode uses a node service to create a live website. 
- React is just an index.html file that uses Javascript to render to the browser.

`npm run build` - executed from the root folder of your React application will output a “static website”.

### Deploying to GitHub Pages
- Enable GitHub Pages on your domain, using the gh-pages branch
- Create Personal Access Token in your GitHub account
- Add token as a “Secret” called PERSONAL_TOKEN in the repository housing your react app
- Add react workflow .yml file to your repository (in .github/workflows)
- This will initiate a GitHub Action whenever you push (or merge) code into your repository. 
- This action will run the build command for you, create a new branch called gh-pages and deploy your React static files

### Deploying to AWS (s3)
- Create a new Bucket
  - Storage containers for static assets
  - Essentially, these are “folders”
- Objects
    - These are the things in the buckets (your files)
    - Upload the contents of your React application build folder to your bucket
- Set up to serve websites
  - Properties Tab “Static Web Hosting” option

### Deploying to AWS Amplify
- Create a new Amplify Workflow
- Point the workflow at your GitHub repository (master branch)
- Merge your code to master on GitHub
- Amplify will monitor your repository for changes, pull, build, and deploy your React app automatically

### Deploying to Netlify
- Create a netlify.com account
- Create a new application
- Point the application at your GitHub repository (master branch)
- Merge your code to master on GitHub
- Netlify will monitor your repository for changes, pull, build, and deploy your React app automatically

### Deploying to an “old school” host, such as godaddy.com
- Create your account
- Open an FTP connection to your hosting company with a tool like Transmit or FileZilla
- Navigate to the web root folder
- Upload the contents of your react application’s build folder
