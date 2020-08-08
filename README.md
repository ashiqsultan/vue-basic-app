# Table of Contents
- [General](#general)
  * [Single File Component Nature of Vue](#single-file-component-nature-of-vue)
    + [Pure JavaScript file vs .Vue file](#pure-javascript-file-vs-vue-file)
    + [Why use .vue file instead of .js](#why-use-vue-file-instead-of-js)
  * [Vue Component Properties](#vue-component-properties)
- [Template](#template)
  * [Interpolation {{ }}](#interpolation------)
  * [Directives v-directive](#directives-v-directive)
    + [v-bind](#v-bind)
    + [v-model](#v-model)
  * [Events](#events)
    + [v-on](#v-on)
- [Methods](#methods)
  * [Access data from Method](#access-data-from-method)
- [Watch Component Property](#watch-component-property)
- [Props](#props)
  * [Prop Types](#prop-types)
  * [More than one Prop type:](#more-than-one-prop-type-)
  * [Make a Prop Required and Default Value](#make-a-prop-required-and-default-value)
  * [Prop Validator](#prop-validator)
    + [Valid Prop types](#valid-prop-types)
  * [Passing a Prop](#passing-a-prop)
- [VueX](#vuex)
  * [General](#general-1)

# General
This is a basic Vue app containg all important features created for learning purpose. Run the app in dev mode and look into the MyComponent.vue file.
## Single File Component Nature of Vue

### Pure JavaScript file vs .Vue file

A Vue component can be declared in a JavaScript file ( .js ) like this: This can only have js code

```jsx
Vue.component('component-name', {
/* options*/
props: ['name'],
template: '<p>Hi {{ name }}</p>'
*})
// The template is inside the options because*
```

or also  it can be specified in a .vue file.

```jsx
*new Vue({
/* options */
})
```

### Why use .vue file instead of .js

The .vue file is pretty cool because it allows you to 

- Define JavaScript logic
- HTML code template
- CSS styling

all in just a single file, and as such it got the name of Single File Component.

```jsx
<template>
// HTMML code here
</template>

<script>
export default {
	data() {
		return {
			hello: 'Hello World!'
		}
	}
}
</script>

<style>
// CSS goes here
p {
color: blue;
}
</style>
```

## Vue Component Properties

- el
- props
- template
- data
- methods
- computed
- watch
- created() (this is like onCreated or useEffect method in React)

# Template

- Vue.js uses a templating language that's a superset of HTML. We can use
interpolation, and directives. This article explains directives.
- Any HTML is a valid vue template
- We will see about **Interpolation** and **Directives**

## Interpolation {{ }}

- It is using {{ }} in the html template.
- You can also use only a single line of JS code inside the {{ }}} interpolation of a template
- But avoid using logic in templates instead try moving them to component methods
- **The value included in any interpolation will be updated upon a change of any of the data
properties it relies on.**

## Directives v-directive

Just like how Interpolation can be used in Vue templates, Directives, are basically like HTML attributes which are added inside templates. They all start with v- , to indicate that's a Vue special attribute.

We will see some important v-directives

### v-bind

Interpolation only works in the tag content. You can't use it on attributes.

Attributes must use v-bind

```jsx
<a v-bind:href="url">{{ linkText }}</a>
// Short hand
<a :href="url">{{ linkText }}</a>
```

### v-model

Using v-model we can change the Component data. It will be used in HTML elements which accept inputs to change the component data

```jsx
<template>
  <div>
    <p>Hello this is my compnent</p>

    <input v-model="enteredMessage" placeholder="Enter a message" />
    <p>Message is: {{ enteredMessage }}</p>

    <select v-model="selectedFruit">
      <option disabled value>Choose a fruit</option>
      <option>Apple</option>
      <option>Banana</option>
      <option>Strawberry</option>
    </select>
    <span>Fruit chosen: {{ selectedFruit }}</span>

  </div>
</template>

<script>
export default {
  name: "MyComponent",
  data() {
    return {
      selectedFruit: null,
      enteredMessage: null,
    };
  },
};
</script>
```

## Events

Vue.js allows us to intercept any DOM event by using the v-on directive on an element.

### v-on

- It is for implementing on click listener functionality

```jsx
<a class="btn btn-primary" v-on:click="handleClick">Click me for OnClick event</a>
export default {
methods: {
    handleClick() {
      alert("test alert");
    },
  },
}
```

- v-on is so common that there is a shorthand syntax for it, @ :

```jsx
<a v-on:click="handleClick">Click me!</a>
<a @:click="handleClick">Click me!</a>
```

- **Event directive modifiers**. One good example is .prevent , which automatically calls preventDefault() on the event.

```jsx
<form v-on:submit.prevent="formSubmitted"></form>
```

Other modifiers include .stop , .capture , .self , .once , .passive and they are described
in details in the official docs.

# Methods

```jsx
<script>
export default {
	methods: {
		handleClick: function(text) {
			alert(text)
		}
	}
}
</script>
```

## Access data from Method

`this.propertyName`

# Watch Component Property

- Its an Object
- It watches for changes to the component data
- The data name and the watch name should have the same name

# Props

Props are the way components can accept data from components that include them (parent
components).

```jsx
<script>
export default {
props: ['firstName', 'lastName'],
}
</script>
```

## Prop Types

You can specify the type of a prop very simply by using an object instead of an array, using
the name of the property as the key of each property, and the type as the value:

```jsx
<script>
export default {
	props: {
		firstName: String,
		lastName: String
	},
}
</script>

```

## More than one Prop type:

```jsx
props: {
	firstName: [String, Number]
}
```

## Make a Prop Required and Default Value

```jsx
props: {
	firstName: {
		type: String,
		required: true
		default: 'Unknown person'
	}
}
```

## Prop Validator

```jsx
props: {
	name: {
		validator: name => {
			return name === 'Flavio' //only allow "Flavios"
		}
	}
}
```

### Valid Prop types

- String
- Number
- Boolean
- Array
- Object
- Date
- Function
- Symbol

## Passing a Prop

If its a static value

```jsx
<ComponentName color="white" />
```

If its from Component data we should use **`v-bind:`** or `:dataname`

```jsx
<template>
	<ComponentName :color=color />
</template>
<script>
...
export default {
//...
	data: function() {
		return {
			color: 'white'
		}
	},
//...
}
</script>
```

# VueX

Components in Vue.js out of the box can communicate using

- props, to pass state down to child components from a parent
- events, to change the state of a parent component from a child

## General

- Create a folder named store inside src folder
- Create an index,js file inside the store folder. This is the entry point for the store
- The index.js will have a variable called module. Which contains

```jsx

const state = {
};

const getters = {
};

const actions = {
};

const mutations = {
};

export default {
  state,
  getters,
  actions,
  mutations
};
```
# Other Tips
## Vue Global Prototype variables 
```
Vue.prototype.$yourVariableName = yourValue
```
You can now access $yourVariableName anywhere from your app. This can be used for global variables

### state
It contains the data
### getters
- It's used to get a state data.
- Its like a middle man which we use to get the data stored in the state.
- Using getters we can modify how we want to view the state data without changing the actual data
### mutations
- They are used to modify the state data
- In the components we will run a mutation functions ny running **commit**
- Using `{strict:true}` in the Store options will restrict modification of state without using mutations
### actions
- Actions are like a bridge between components and mutations
- Actions are dispatched like how mutations are commited
