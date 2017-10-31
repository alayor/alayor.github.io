---
layout: post
title:  "Creating a React Component using TDD"
date:   2017-10-01
categories: post
comments: true
excerpt_separator: <!--excerpt_end-->
image: /assets/images/react.jpg
---

Nowadays it's almost mandatory to use TDD in every new piece of software in
order to avoid creating **<a href="https://en.wikipedia.org/wiki/Legacy_code" target="_blank">legacy</a>** code.

There are many tools available to create unit tests in JavaScript and ReactJS.

In this post we will be using **<a href="https://facebook.github.io/jest/" target="_blank">jest</a>**
and **<a href="http://airbnb.io/enzyme/" target="_blank">enzyme</a>** to create a simple React Component
using Test-driven Development.

<!--excerpt_end-->
![Required](/assets/images/react.jpg)

This example was created using the following versions:
{% highlight javascript %}
{
  "react": "15.4.0",
  "react-dom": "^15.6.1",
  "enzyme": "^2.9.1",
  "jest": "^21.0.1"
}
{% endhighlight %}
The first step is to create a failing test that will try to render a React
Component using the `shallow` function from `enzyme`.

<span style="color:red">Red</span>
{% highlight javascript %}
// MyComponent.test.js
import { shallow } from 'enzyme';
describe("MyComponent", () => {
  it("should render my component", () => {
    const wrapper = shallow(<MyComponent/>);
  });
});
{% endhighlight %}

```
Should render component
   ReferenceError: MyComponent is not defined
```

<span style="color:green">Green</span>
{% highlight javascript %}
// MyComponent.js
class MyComponent extends React.Component {
  render() {
    return <div />;
  }
}
export default MyComponent;
{% endhighlight %}

Enzyme creates a `snapshot` which represents how the component is being rendered.
We can add a component as child by changing this snapshot first and then
asserting it by using the method `toMatchSnapshot()`.

<span style="color:red">Red</span>
{% highlight javascript %}
// MyComponent.test.js.snap
exports[`MyComponent should render initial layout 1`] = `
Array [
  <MyForm />,
]
`;
{% endhighlight %}

{% highlight javascript %}
// MyComponent.test.js
it("should render initial layout", () => {
  // when
  const wrapper = shallow(<MyComponent/>);
  // then
  expect(wrapper.find('div').children().nodes).toMatchSnapshot();
});
{% endhighlight %}

```
Should render initial layout
   expect(value).toMatchSnapshot()
   Received value does not match stored snapshot 1.
```

<span style="color:green">Green</span>
{% highlight javascript %}
// MyComponent.js
class MyComponent extends React.Component {
  render() {
    return <div>
      <MyForm />
    </div>;
  }
}
export default MyComponent;
{% endhighlight %}

We can then pass a function to the child component as a prop. We first change
the snapshot to make the test fail. After that, we add the prop in `<MyForm>`.

<span style="color:red">Red</span>
{% highlight javascript %}

// MyComponent.test.js
exports[`MyComponent should render initial layout 1`] = `
Array [
  <MyForm
    onChange={[Function]}
  />,
]
`;
{% endhighlight %}
```
expect(value).toMatchSnapshot()
 Received value does not match stored snapshot 1.
```
<span style="color:green">Green</span>
{% highlight javascript %}
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
{% endhighlight %}

Then, we make sure that the method `updateState` is executed after the
function `onChange` its called in the child.

<span style="color:red">Red</span>
{% highlight javascript %}
// MyComponent.test.js
it("should execute function passed to form", () => {
  // given
  jest.spyOn(MyComponent.prototype, 'updateState');
  const form = shallow(<MyComponent />).find('MyForm');
  // when
  form.props().onChange();
  // then
  expect(MyComponent.prototype.updateState).toHaveBeenCalled();
});
{% endhighlight %}
```
TypeError: Cannot read property _isMockFunction_ of undefined
```
This indicates that we need to add the `updateState` method to the component.

<span style="color:green">Green</span>

{% highlight javascript %}
// MyComponent.js
class MyComponent extends React.Component {
  updateState() { // <-- new method
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
{% endhighlight %}
After executing the same test again we get a new error indicating that the function
didn't get called. We make it pass by passing this function to the child.

<span style="color:red">Red</span>
```
expect(jest.fn()).toHaveBeenCalled()
Expected mock function to have been called.
```
<span style="color:green">Green</span>
{% highlight javascript %}
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
{% endhighlight %}
We now have a simple React Component created using pure TDD.

This process may seems slow at the beginning.
However, we gain a lot more in the long run.

TDD allows us to create well founded software that speeds up the maintenance
process and reduce its cost.
