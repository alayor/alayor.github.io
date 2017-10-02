---
layout: post
title:  "Creating a React Component using TDD"
date:   2017-10-01
categories: post
comments: true
excerpt_separator: <!--excerpt_end-->
---

It's become mandatory to use TDD in every new piece of code we write if
we want to avoid creating legacy code from the beginning.

We have many tools available to create unit tests in javascript and some other
nice tools intended for React and the Flux architecture.

In this post we will be using `jest` and `enzyme` to create a simple React Component
using Test-driven Development.

<!--excerpt_end-->

This example was created using the following versions:

`"react": "15.4.0"`

`"react-dom": "^15.6.1"`

`"enzyme": "^2.9.1"`

`"jest": "^21.0.1"`

* The first step is to create the component.

<span style="color:red">Red</span>
```javascript
// MyComponent.spec.js
import { shallow } from 'enzyme';
describe("MyComponent", () => {
  it("should render my component", () => {
    const wrapper = shallow(<MyComponent/>);
  });
});
```
```
MyComponent › should render component
   ReferenceError: MyComponent is not defined
```
<span style="color:green">Green</span>
```javascript
// MyComponent.js
class MyComponent extends React.Component {
  render() {
    return <div />;
  }
}
export default MyComponent;
```
* We then make sure the component matches a predefined snapshot by making
sure it contains another React Component.

<span style="color:red">Red</span>
```javascript
// MyComponent.spec.js.snap
exports[`MyComponent should render initial layout 1`] = `
Array [
  <MyForm />,
]
`;
```
```javascript
// MyComponent.spec.js
it("should render initial layout", () => {
  // when
  const wrapper = shallow(<MyComponent/>);
  // then
  expect(wrapper.find('div').children().nodes).toMatchSnapshot();
});
```
```bash
MyComponent › should render initial layout
   expect(value).toMatchSnapshot()
   Received value does not match stored snapshot 1.
```
<span style="color:green">Green</span>
```javascript
// MyComponent.js
class MyComponent extends React.Component {
  render() {
    return <div>
      <MyForm />
    </div>;
  }
}
export default MyComponent;
```
* We can then specify a function passed to the child component as a prop. For this
we need to change the snapshot.

<span style="color:red">Red</span>
```javascript
// MyComponent.spec.js
exports[`MyComponent should render initial layout 1`] = `
Array [
  <MyForm
    onChange={[Function]}
  />,
]
`;
```
```
expect(value).toMatchSnapshot()
 Received value does not match stored snapshot 1.
```
<span style="color:green">Green</span>
```javascript
// MyComponent.js
class MyComponent extends React.Component {
  render() {
    return (
    <div>
     <MyForm
      onChange={() => {}} />
    </div>
  );
  }
}
export default MyComponent;
```
* Then, we can make sure that the function is executed when it's called inside
the form

<span style="color:red">Red</span>
```javascript
// MyComponent.spec.js
it("should execute function passed to form", () => {
  // given
  jest.spyOn(MyComponent.prototype, 'updateState');
  const form = shallow(<MyComponent />).find('MyForm');
  // when
  form.props().onChange();
  // then
  expect(MyComponent.prototype.updateState).toHaveBeenCalled();
});
```
```
TypeError: Cannot read property '_isMockFunction' of undefined
```
This last error is caused by the missing function we want to pass to
the child component. We create this method to green out the cycle.

<span style="color:green">Green</span>
```javascript
// MyComponent.js
class MyComponent extends React.Component {
  updateState() {
  }
  render() {
    return (
    <div>
     <MyForm
      onChange={() => {}} />
    </div>
  );
  }
}
export default MyComponent;
```
After executing the same test again we get a new error indicating that the function
didn't get called. We makw it pass by just passing this function to the child.

<span style="color:red">Red</span>
```
expect(jest.fn()).toHaveBeenCalled()
Expected mock function to have been called.
```
<span style="color:green">Green</span>
```javascript
// MyComponent.js
class MyComponent extends React.Component {
  updateState() {
  }
  render() {
    return (
    <div>
     <MyForm
      onChange={this.updateState} />
    </div>
  );
  }
}
export default MyComponent;
```
<!--excerpt_end-->
