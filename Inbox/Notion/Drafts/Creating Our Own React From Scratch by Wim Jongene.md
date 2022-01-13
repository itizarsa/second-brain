# Creating Our Own React From Scratch | by Wim Jongeneel | Aug, 2021 | ITNEXT

Status: Unprocessed
URL: https://itnext.io/creating-our-own-react-from-scratch-82dd6356676d

![https://miro.medium.com/max/1200/1*fggC8t551kI30A-X0GYWDA.jpeg](https://miro.medium.com/max/1200/1*fggC8t551kI30A-X0GYWDA.jpeg)

---

![Creating%20Our%20Own%20React%20From%20Scratch%20by%20Wim%20Jongene%2076b37b9b36d040e7ba53355c45253dbb/1fggC8t551kI30A-X0GYWDA.jpeg](Creating%20Our%20Own%20React%20From%20Scratch%20by%20Wim%20Jongene%2076b37b9b36d040e7ba53355c45253dbb/1fggC8t551kI30A-X0GYWDA.jpeg)

Photo by [Johannes Plenio](https://unsplash.com/@jplenio?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/virtual-tree?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

In the past decade we have seen massive changes in the way how web applications are developed. Where in the past an interface would have been generated on the server with only some minor scripting on the client-side, these days it is standard to use one of the various reactive render libraries to create complex stateful client-side applications.

While many developers are without doubt very good in utilizing libraries like React or Vue to create rich user interactions, the understanding of their exact inner workings is far less wide spread. In this article I want to take you on a journey to create our very own reactive render library and in this way demystify what goes on underneath the hood of those very impressive tools.

But before we start, a small word of warning. While our library very much will work (see the sample applications at the end), it is meant as a demonstrative tool, not a lightweight alternative to React. The entire project can also be found on [GitHub](https://github.com/WimJongeneel/ts-reactive-rendering).

# 1. The architecture of a reactive render library

The main things inside any reactive render library are the components. It is the job of a component to manage a so-called ‘reactive scope’. This means that a component contains a variable (the ‘state’) and is responsible for rendering that variable into the DOM. Here we already see some of the concepts you might know from writing react components: `this.state`, `this.setState` and `render`.

The architecture of a basic reactive component. Every interaction creates a new state, which creates a new VDOM, which updates the HTML of the application (Image by author)

A critical point in reactive way of thinking is that we don’t specify DOM modifications for each and every thing that can happen to our applications state (like you would see in a jQuery code base). Instead there is one render function and that render function gets used every time some change happens to the state. While the idea of ‘just one render function’ is great (less code, no state in the DOM etc) it does raise another issue: if we would just replace the entire DOM structure on every update we would create quite a lot of issues. Outside of any performance losses, it would destroy any focus the user has, create weird jumps in scrolling and so on.

To prevent those things from happening reactive render libraries use a virtual DOM with a diffing algorithm to first generate an update strategy that can be applied to the real DOM. Inside this virtual DOM we can re-render things as much as we like, it is just a JavaScript object with a fancy name, not the real DOM. And with a smart diffing algorithm we can make sure that there are as few modifications made to the real DOM as possible, making the actual DOM modifications properly even more efficient then any manually written DOM update function.

I will start this article of with the implementation of such a virtual DOM. Of course this one will be a lot simpler that what you will find in for example the React source code, but it will do the same things reasonably well and more importantly, demonstrate the inner workings of a virtual DOM. After this we will look into creating stateful components with state and props, and how the concept of stateful components plays with the virtual DOM. To close of I will show you the library in action with some real sample applications.

# 2. The Virtual DOM

In its essence a virtual DOM exists of two data structures: the HTML syntax tree and the diff tree. The HTML tree represents the state of the HTML in a JavaScript object. It is the return type of the render method of components and what the developer that uses the library will interact with. The diff tree describes which steps need to be taken to update a HTML element from the state of one syntax tree to another.

The relation between the VDOM trees, the diffing algorithm and the diff (Image by author)

## 2.1 The HTML syntax tree

This data structure will store the state of our virtual DOM. At this moment we will only support normal elements and text nodes. Later on this will be extended to allow stateful components to be used inside the tree. The type definition can be found below. The key property will be used when diffing child elements, people familiar with React will already have recognized this.

The VDOM type definition

Our library will not support JSX, so we need some helper functions to create VDOM elements in a convenient way. Those function are what will be used in the render methods of our components. They are the equivalent of the `React.createElement` calls you might have seen in your JavaScript bundles.

The functions to create VDOM elements

## 2.2 The diff data structure

We will first start of with a diffing mechanism that works on a single element and after that we will expand it with support for child elements. First we will create a type with all the operations. An operation is a DOM mutation that will be made to a single HTML element. The primary operations are `update` and `replace`. Next to those we also have a `skip` operation that is used to indicate that no modification has to be done.

The types for the operations that can be applied to a single element

The `update` operation contains an actual diff tree and exists of the small steps that need to be taken to process the result of most of the `setState` calls. Here you also see a reference to the updates for the child elements. The operations for the child elements are a little bit different because they will be applied to a collection of elements. Outside of the operations that we already defined they also include `insert` and `remove`:

The types for the operations that can be applied to a the child elements of an element

# 3. Creating diffs

Now we are able to construct a virtual DOM and a diff it is time to create what makes a VDOM worth the effort: the diffing algorithm. This is what will allow our components to effectively transition between their states and is the single most critical thing when it comes to the smoothness of a reactive application. A slow or even broken diffing algorithm will completely destroy the user experience of any application, no matter how carefully crafted the actual components are.

We will tackle this piece in two parts: first the diffing of an individual element and after that the diffing of a collection of (child) elements, just like we did for the type definitions.

## 3.1 Creating the diff of an element

When diffing our VDOM we have to deal with two different things that can update: text nodes and HTML elements. I will start of by dealing with text nodes, as they are pretty straight forward. If both elements are text nodes and the value hasn’t changed we return a `skip` operation. If we have a text node in any other case we will have to replace the old element with the new one:

The diffing of text nodes

After those checks have ran we are sure that both of the nodes are regular elements. However, we still have one case left in which we have to completely replace the node: when the `tagname` of the old and new element are different. This is the next case we will add to our function:

An updated tagname means that the entire component has to be remounted

Now we can be sure that the two elements we have are of the same type and can be updated from one state to the other without having to create a new element. To do this we have to generate three different things: the attributes that have been removed, the attributes that need to be set and the updates for the children:

Generating all the data for the update operation

With this we have completed the diffing logic for single elements. Just like with the HTML syntax tree, we will add support for component diffing and mounting later on in the article. Now it is time to move on to the diffing logic for the child elements.

## 3.2 Creating the diff for the children

The last part of the diffing algorithm is the diffing for the child elements. This is by far the most complicated part of a VDOM, because there are many different things that could have happened to the children of an element. For example: we could have inserted a new element at the start, somewhere in the middle or at the end. We could also have removed elements, updated elements or resorted the existing elements. This is where the `key` of an element comes into play: we assume that if the keys are the same the elements are the same (but could still be modified). With the keys we can identify that the first element in the current tree corresponds with the third element in the new tree because we added two new elements at the front. Without keys this would practically be impossible to know.

An example with the operations of the diff between two collections of VDOM elements (Image by author)

To keep things simple we will go for a bit of a simplified implementation that doesn’t support the reordering of keys (if you reorder it will `remove` and `insert` the children that are out of order). This saves a lot of code that isn’t that interesting, but in case this really interests you feel free to add your own implementation. We will start our function of by creating two stacks with the remaining unprocessed children for the old and new tree:

The base structure for the childsDiff function

On line 6 we will add the logic that processes all the children and fills the `operations` array with the operations that are needed to transform from the old tree to the new one. This algorithm will center around finding elements (= keys) that are present in both the old and new VDOM. For those elements we need to generate updates while all other elements either get removed or inserted. Shown below is this part of the logic. As long as there are updated children left in the stacks we keep generating `update` operations for them.

When diffing the child elements we are mainly concerned with generating update operations for updated elements to prevent remounts of existing elements

An important thing to note in this function is that the `nextUpdatedKey` doesn’t have to be the first element of both the `remainingOldChilds` and the `remainingNewChilds`. There can be elements present before them in the stacks that either have been removed or inserted and thus aren’t present in both collections. To deal with this we first have to remove all old elements and insert all new elements before we can create the update.

Old elements have to be removed and new elements have to be inserted before we can append an update operation to our result

The final part we have to account for is that there still can be elements remaining after all updated nodes have been processed. This happens when there are children either added or removed at the bottom of the tree. This final bit of code can be found below.

Finally we have to process the remaining remove and insert operations after all the updates have been processed

With this addition we now have a complete diffing algorithm that is capable of generating keyed diffs of complex trees and will come up with a reasonable efficient diff. There are a lot of optimizations possible, for example every pair of a `remove` and `insert` could be done with a single `replace`. Next to this you could also support resorting of elements based on their keys, something that could be a solid requirement for some applications.

An example of resorted keys. In this case B will be removed and inserted. If B is a stateful component this will mean that B gets reset to its initial state (Image by author)

# 4. Connecting the virtual and real DOM

Now we have a completed virtual DOM it is time to connect it with the real DOM. For this we will need two separate parts: a function that takes a VDOM and renders it into the DOM and a function that accepts a diff and applies it to an element in the DOM.

The relation between the diff, the HTML element and the apply function (Image by author)

## 4.1 Rendering a virtual DOM

The first thing we need to start using our brand new virtual DOM is a way to render it into the actual DOM. This function will be used to render the first version of a component. After this it will be the `applyDiff` function that is responsible for connecting the virtual and real DOM with each other. This function essentially boils down to a `document.createElement` call for each element in the tree:

Converting the VDOM into an HTML element

A thing worth noting here is that we assign every property directly to the element. This is of course not how the likes of React have implemented this logic. The proper way of doing it would include setting attributes with `setAttribute` and using a synthetic event system to connect the events in the DOM with events in the VDOM. This is one of the places where I cut a corner to keep this article somewhat reasonably sized.

## 4.2 Applying a diff to a HTML element

The other half of the rendering is the application of the diff. This function will take a `HTMLElement` and a diff and apply it to the element. Here you see the same operations as we defined earlier. For the sake of brevity I have left out all the validation TypeScript would let me, the only thing we validate is if we are assigning attributes to an actual element and not a text node.

Applying the diff between two VDOM elements to a DOM element

In `applyChildrenDiff` we loop over the operations and apply those to the current child element. Most of the complexity here is related to the `offset` that is used to know which element in the DOM is the element the current operation does relate to. Here it is important to remember that there can be way more operations then there are child elements.

Applying a collection of operations to the child elements of a HTML element

With this function we have concluded the VDOM and everything related to it. The next leg of our journey is to add stateful components into the mix and combine those into a true reactive application.

# 5. Components and reactive scopes

Many people that are familiar with React will know components as things that contain a state. And while from an users perspective this is indeed the important part of components, within the source code of a reactive framework the main job of a component is to manage a reactive scope. So what is a reactive scope? A reactive scope is a part of the VDOM tree that is responsible for its own updates. This means that a component has a reference to a html element in to DOM where it is mounted and creates the diffs for this element based on the state and props. Even when the component is owned by a parent component it will still be responsible for its own rendering and diffing.

The lifecycle hooks for our components (Image by author)

## 5.1 Creating the component class

We will start this of by laying out the base class for all components. This class will store the current props, state, root element and VDOM. The basic outline for this class can be found below. Many of the attributes and methods will be familiar from libraries like React, for example `props`, `state`, `setState`, `componentDidMount` and `render`.

There are also some methods that are indented for internal use only. `setProps` will be called during updates of the parent component to provide this component with new props. This function returns the diff between its VDOM and the new VDOM to its parent. `initProps` will be called during the mounting process and returns the initial VDOM that will be rendered in the real DOM. When this is done `notifyMounted` will be called and the component will be completely mounted in the DOM. Next to this we also have an `unmount` method that will be used when the components gets removed from the DOM.

The outline for the Component class

Another thing you see are the empty hook methods that individual components can override. We will wire those up to the internals of our library as we go along.

## 5.2 Mounting components

The first step to start using components inside a render function is to extend the VDOM with a node type for components. This will enable us to use a component inside the render function of another component and thus create a real component tree with multiple stateful components. Inside the render function the developer will specify what component should be rendered and with which props. The type definition for this kind of node is shown below.

The extension for the definition of the VDOM for components

The `instance` property is only for internal usage. This will store the actual instance of the component, with the state etc. inside of it. Inside the diffing function we will make sure to copy the existing component instances over from the old to the new tree so they are preserved between the trees. It is important to note that a render function of a component will not create any instances of the child components. Instead it will return a node with a reference to the component class and a value for the props. The constructing of the component will be done behind the scenes.

The function to construct a component node in a render function

The first scenario of a component being used in the VDOM that we will consider is the initial rendering of a component. This happens when a component is either the root component of an application or is present at the first render of its parent component. Later on we will look into what happens if a component replaces an existing element in the VDOM.

When it comes to ‘mounting’ a component there are two further sub-cases to consider: the component already has been instantiated or still needs to be created. When a component already has an instance the process is fairly straight forward: we call the `render` function to get the current VDOM representation of its state, create an HTML element from it and call `notifyMounted` on the component.

Everything that happens during the mounting of a component in the render function, split between the responsibilities of the render function and the component class. The arrows down are calls from the render function, the arrows up are returns from the methods

When a component still needs to be created there are a few more steps involved. First we will create a component instance by using the `new` keyword. This instance gets assigned to the `instance` prop of the VDOM. In this way it is preserved to be used on the next render so we don’t keep recreating our stateful components. After this we initialize the props of the component. This will return the initial VDOM of the component that we can render into the DOM. Finally we also call `notifyMounted`. The additional code that implements this logic for the `renderElement` function is shown below.

Mounting a component in the render function

To make this actually work we have also to implement the various methods in the component class. The first method we will tackle is `initProps`. This method is responsible for initializing the `props` and executing the first `render`. It will store and return the resulting VDOM tree to the caller. The caller will then be responsible for putting it into the DOM.

The initialization of the props in a component

The other method we need to finish up the mounting process is `notifyMounted`. This is the callback that will be called by `render` (potentially via `applyUpdate`) at the moment we have created a HTML element for the initial VDOM tree. This method will also call `componentDidMount`, a hook that components can implement to do something after the moment got rendered into the DOM. This is done within a `setTimeout` to ensure the hook is called after the current function is done mounting the component, not during the mounting.

The callback for the rendering and the componentDidUpdate hook

## 5.3 Updating a component

Now we are able to mount components into the DOM it is time to start dealing with updating them. There are two ways in which an update can happen: the component can update its `state` or it can get new `props` from its parent. In the first case it is the component that is responsible for applying the update to the DOM, in the latter case it will return a diff to its parent.

But in both cases the process is very similar: we render the component, create a diff with this new tree and the saved existing one, update the `currentRootNode` with the new VDOM tree and return the diff. The implementation of this is shown below. The `getUpdateDiff` method will be used by both `setState` and `setProps` and does the heavy lifting of managing the reactive scope of a component. This is also the place where we schedule the call to `componentDidUpdate` to be ran after the update completes.

Generating update between the current state of the component and the previous result of the render method

One additional thing you see here is a `callback` on `replace` operations. This is needed to make sure that the `mountedElement` property of our component keeps pointing to the correct HTML element in case the root element gets replaced. For this we need a few additions to the VDOM and the rendering:

Adding callbacks to the replace operation and applyUpdate function

## 5.4 Updating components with setState

When a component gets updated via `setState` there are three things we need to do: set the `state` property, get a diff with `getUpdateDiff` and apply this diff to the `mountedElement`. Next to this I also added an if-statement to throw an error if you attempt to update a unmounted component. Instead of this you could also just update the state and return after that, then the new state would be used during the first render in `initProps`. You might recognize this as a warning from React. Because we already implemented all the logic for updating components this method is now fairly short and simple:

The rather famous setState method for our components

## 5.5 Updating components with setProps

The other way in which a component can get updated is via `setProps`. This method is in essence very similar to `setState`. You can find its complete definition below. Here we also throw an error if the component hasn’t been mounted yet. One difference with the classic React lifecycle hooks is that we allow `componentWillRecieveProps` to return a new state that will be used before we re-render the component with the new props.

The method the parent component will use for updating the props of a component

In contrast to `setState`, `setProps` does get called in the diffing function when the props of a component node have changed. To make this actually happen we will add component support to the diffing. There are three things that there can happen to a component during this process: we update an existing component, we unmount an existing component or we mount a new component.

An overview of what happens when a component with a child component updates. Note that the parent component doesn’t diff the VDOM of the child, but the parent is however responsibly for applying the diff the child component has generated

The scenario we will implement first is the updating of an existing component. First step is to copy the existing instance from the `oldNode` to the `newNode`. After this we check if the `props` have changed and if so, set the `props` of the component. The resulting diff of this is the diff we directly return from our function. In case the `props` didn’t change we return a `skip` operation.

Updating the props for an existing component inside the diffing code

The second scenario we will implement is the replacement of any node by a component. This is fairly similar to the mounting we already saw, but now done inside the diffing function to generate a `replace` operation. The noteworthy thing here is that we use the `callback` of the `replace` operation to make sure `notifyMounted` is still called inside the render function.

Mounting a component inside the diffing

## 5.6 Unmounting components

The final scenario is the replacement of a component with something else. This leads to the ‘unmouting’ of a component. During the unmouting several things need to happen: we call `unmount` on the component, the component invokes the `componentWillUnmount` hook, the component nulls its reference to the DOM and finally we actually remove the HTML element from the DOM.

The update to the diffing code to unmount components that will be removed

The final method to implement of our component is `unmount`. This method call the `componentWillUnmount` hook, this time without a `setTimeout` because we want to run the hook before the actual unmounting. Next to that we set the `mountedElement` to null. This has two reasons: any updates to this component will now give an error and it ensures that the HTML element is freed up to the garbage collection.

The unmounting of a component

This does finally conclude the code of our reactive rendering library. With all the parts we now have it is possible to create real modern single-page-applications.

# **6. Building a sample application**

In this final chapter I will show you an example application that has been made with the library presented in this article. Just like every example application ever it is of course a Todo list. The first component of this application shows you a standard controller form. The second component uses this component in its render function and renders a list with all added items.

A controlled form component with our reactive render library

A simple todo app with our reactive render library

Outside of the missing JSX support this code should look familiar to anyone who has ever worked with React. As you can see, our library supports most of the primary features of something like React and is totally capable of powering small applications.

# 7. Conclusion

If you made it this far, thanks for reading! I hope this exercise helps you understand how reactive rendering works under the hood. The complete source code can be found in [this repository](https://github.com/WimJongeneel/ts-reactive-rendering).