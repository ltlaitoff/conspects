
# What is vue?

Vue is JavaScript framework fow building user interfaces. It build on top of standarts HTML, CSS and JavaScript and provides a declarative and component-based programming model.

Minimal example:
```js
import {createApp } from 'vue'

const App = {
  data() {
    return {
      count: 0
    }
  }
}

const app = createApp()
app.mount('#app')
```

```vue
<div id="app">
  <button @click="count++"> Count is: {{ count }} </button>
</div>
```

The above example demonstrates the two core features of Vue:
- Declarative Rendering: Vue extends standart HTML with a template syntax that allows us to declarative describe HTML outpuit based on JavaScript state
- Reactivity: Vue automatically tracks JavaScript state changes and efficiently updates the DOM when changes happen

## Single-File components

In most build-tool-enabled Vue project, we author Vue components using an HTML-like file format called Single-File Component (also known as `*.vue` files, abbreviated as **SFC**). A Vue SFC, as the name suggests, encapsulates the component's logic (JavaScript), template(HTML), and styles(CSS) in a single file. Here's the previous example, written in SFC format:
```vue
<script>
export default {
  data() {
    return {
      count: 0
    }
  }
}
</script>

<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>
```

SFC is a defining feature of Vue and is the recommended way to author Vue components **if** your use case warrans a build setup.

## API Styles

Vue components can be authored in two different API styles: **Options API** and **Composition API**.

### Options API

With Options API, we define a component's logic using an object of options such as `data`, `methods`, and `mounted`. Properties defined by options are exposed on `this` inside functions, which points to the component instance:

```vue
<script>
export default {
  // Properties returned from data() become reactive state
  // and will be exposed on `this`.
  data() {
    return {
      count: 0
    }
  },

  // Methods are functions that mutate state and trigger updates.
  // They can be bound as event listeners in templates.
  methods: {
    increment() {
      this.count++
    }
  },

  // Lifecycle hooks are called at different stages
  // of a component's lifecycle.
  // This function will be called when the component is mounted.
  mounted() {
    console.log(`The initial count is ${this.count}.`)
  }
}
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

### Composition API

With Composition API, we define a component's logic use imported API functions. In SFCs Composition API is typically used with `<script setup>`. The `setup` attribute is a hint that makes Vue perform compile-time trransforms that allow us to use Composition API with less boilerplate. For example, imports and top-level variables / functions declares in `<script setup>` can directly usable in the template

Here is the same components, with the exact same template, but using Composition API and `<script setup>` instead:

```vue
<script setup>
import { ref, onMounted } from 'vue'

// reactive state
const count = ref(0)

// functions that mutate state and trigger updates
function increment() {
  count.value++
}

// lifecycle hooks
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

### Which to Choose?

Both API styles are fully capable of covering common use cases. They are different interfaces powered by the exact same underlying system. In fact, Options API is **implemented on top** of the Composition API! The fundamental concepts and knoweledge about Vue are shared accross the two styles.

The Options API is centered arount the concept of a "components instance" (`this` as seen in the example), which typically aligns better with a class-based mental model for users comming from OOP language background. It is also more beginner-friendly by abstraction away the reactivity details and enforcing code organization via option groups.

The Composition API is centered around declating reactive state variables directly in a function scope and composing state from multiple functions together to handle complexity. It is more free-form and requires to understanding of how reactivity works in Vue to be used effectively. In return, its flexibility enables mode powerful patters for organizing and reusing logic.

* For production use:
	* Go with Options API if you are not using build tools, or plan to use Vue promarily in low-compexity scenarios, e.g. progressive enhancement.
	* Go with Cpomposition API + SFC if you plan to build full applications with Vue.


