> Before you reading this post, please notice that this post is sort of a "insider of docoment". So if you are feel good with you brain power, please read React's official documents directly. You will find all you want about React itself and the elegant thinking behind it.

## List Rendering

When you want to specify keys for you list rendering, the rule of thumb is call the keys in the `map` function.

For instance, look at the snippet below.

{% highlight javascript %}
function ListItem(props) {
    const value = props.value;
    // You shouldn't need to specify the key here
   	return <li>{value}</li>
}
function NumberList(props) {
    const numbers = props.numbers;
    // But put the key here in the `map` function scope
    const listItems = numbers.map((number) => 
		<ListItem key={number.toString()} value={number}/>);
    
	return <ul>{ListItems}</ul>
}
{% endhighlight %}



## Think in React

### Break UI into A Component Hierarchy

For instance, for a product search app, the UI can be split lisk following components hierarchy.

- App (FilterableProductTable)
  - SearchBar
  - ProductTable
    - ProductCategoryRow
    - ProductRow

Luckily, if you are working with a designer, talk to them! For most cases, their PhotoShop layers can simplely become your React components name.



### Build The Static Version of Your React Components

The bese action of build a React components is split the UI and interactivity between each components.

Before we start this section, pleae remember two rules of thumb:

1. **Build the static version costs your more typing but less thinking, while implements interactivity costs your less typing but more thinking.**
2. **DO NOT use `state` at all when you build the static version of your React components.**



### Indentify The Minimal but Full Funcational UI State

Please follow these rules of thumb:

1. **DRY** (Don't Repeat Yourself): Figure out the minimal but complete representation of the state your component needs. For instance, for a TODO application, just keep an array of TODO items around, don't keep a seperate `count` state. If you need it somewhere, simply take the length of the TODO items array.

2. **ATQ** (Ask Three Questions for Each Piece of Data): When you decide on whether a piece of data is `state`, just ask yourself three simple questions:

   - Is it passed from a parent's props?
   - Is it remain unchanged during the component's lifecycle?
   - Is it can be computed through other props or states?

   If you got a "yes" for any of these three questions, then your data may not a `state`.



### Where Our State Should Live

Please following three steps:

1. indentify each components that renders the UI based on each state.
2. find or create a common owner (parent) for above components. 
3. There is where this spcific state should live