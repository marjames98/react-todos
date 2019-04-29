# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) ToDo List Deliverable

## Review


So, we've gone through all of the basics of React. To really hammer it home with practice, let's walk through complete creation of an app. This will be a to-do list, keeping track of everything we need to do for the day (after we finish this!). It's a lot, so we're going to want it to be editable.

This is what it should look like at the end **without styling**:

![list-preview](https://github.com/WDI-SEA/react_state_exercises_global/blob/master/images/todo-list-3.png)


## Getting Started

> This is a good time to check your Activity Monitor program and close all your running node processes. Fresh start!

Use `create-react-app` to create a To-Do list project. `cd` into your folder and run `npm start` to start a server that will serve your new React application!

* Make sure that as you go, you frequently check the site to ensure your changes are all reflecting accurately!

## First, the basic list.

Let's change the name of the component in `App.js` to something more meaningful, like `MyList`. This is just for good practice so we have meaningful component and file names. Make sure to rename your file `App.js` to `MyList.js` to match the name of the component.

Change the contents of the HTML to have a header and the start of a list and an unordered list with one empty list-item.

> Remember to change the name of the component where it's rendered in index.js! You'll also have to change the `import` statement in `index.js`, since you changed the name of the file containing the component that `index.js` is importing from!

Now, our webpage displays an empty list.

Make a component for each item in the list and call it `ListItem`. This component can simply render  `<li>Make the list!</li>` so that we are starting with something in this list.

* Remember to use an `export` statement at the end of the new file to make the code in this file available elsewhere in our application.

* Don't forget to import your `ListItem` component into `MyList.js`.  Then, include the component in what `MyList` renders with `<ListItem />` under the existing header (in place of the existing list item)!


At this point, our app looks like this:

![list-preview](https://github.com/WDI-SEA/react_state_exercises_global/blob/master/images/todo-list-1.png)


## Second, props.

This is a great start - we've already nested components (`ListItem` inside of `MyList`). Now, let's add some props to make this useful and check that current list item off!

Let's first just pass a prop into `ListItem` from `MyList`. We'll call the prop something simple, like `doThis`. 
Make the value different that what you already have so you can make sure your changes are rendering

Then, in `ListItem`, we'll add a list item that uses the `doThis` prop instead of the existing hard-coded text.

Now that we've passed in a prop to `ListItem`, we need to call it in `ListItem.js` using `this.props`

Your app should look like it was in the previous step with a different to-do item.


## Third, render different items in an array.

If we want to make this a truly extensible list, we could create an array of items, pass them into props through the `ListItem` component, and then render each item. Let's do that now.

The easiest way to do this is by using the `map` function. A map is like a `for` loop. With `map`, you make a new variable and iterate through each item in an array with it. It looks like this:


```
let <new_Variable_Name> = <the_Array_We_Are_Mapping>.map( (local_Variable_Name_to_Loop, index) => (
  <what_To_Do_With_Each_Item_in_Loop>
))
```

Here's a simple example that makes a new array by adding an `!` to each element of an array.

```js
const phrases = ['ice cream', 'dinosaurs', 'hobbits']

let excitedPhrases = phrases.map( (phrase, index) => {
  return newPhrase = phrase + '!'
})
// excitedPhrases is ["ice cream!", "dinosaurs!", "hobbits!"]
```

> Note that in the above example, moustaches are used after the arrow rather than the open parentheses in the earlier example.
In ES6, with arrow functions, you can omit the curly brackets and `return` keyword if the return value can be written as a single statement. In the same way that we `return` a single HTML element in a component's `render()` function, we can place this single-statement return value in parentheses and make use of line-breaks without confusing javascript.

##### Plan

* In the `MyList` component, have an array of items for the list—uncreatively called `theList`—that is passed down from `index.js` in the form of a prop
* Create a variable to refer to the new array output by the `map` method, uncreatively but helpfully called `todoItems`.
* Use `map` to iterate through the `todoItems` array, one `item` (this could be any name you'd like) at a time, and use each one to create a `ListItem` component in the `todoItems` list.
* We can later refer to this list by just calling the variable in JSX (like any other variable).  For example, we could say  `{todoItems}`.

##### Implementing the Plan

First, make a list in `index.js`. Make an array of strings that represent your todo items. 
Fill it with what you need to do for the day. Once you've done that, pass that array into your
`<MyList />` component.

The next step is to use the `map` function to create an array of `<ListItem />`s called `todoItems`, each with 
its own `doThis` prop that represents a todo item from `theList`.

<details>
  <summary>Need a hint?</summary>
  
  Here a `map` function call that will create a new array filled with components
  ```jsx
  let iceCreamFlavors = flavorsArray.map((flavorName, index) => (
    <IceCream flavor={flavorName} key={'flavor'+index} />
  ))
  ```
</details>

> NOTE: When you have many children components, it's good to add a `key` section that functions similar to an ID. 

The last step is to call the `todoItems` in the render function of `MyList` class.

<details>
  <summary>Not sure what your component should look like?</summary>
  
  ```jsx
  class MyList extends Component {
    render() {
      let todoItems = this.props.theList.map((item, index) => (
        <ListItem doThis={item} key={'todo' + index} />
      ))

      return (
        <div>
          <h1>Things I should stop procrastinating:</h1>
          <ul>
            {todoItems}
          </ul>
        </div>
      )
    }
  }
  ```
</details>

Your app should now look like the first image!

## Bonus

Do some styling! Try separating your overall styles (like background color) and your component specific styles (like the color of your to-do items) in different css files and importing them.
