# vue-essentials
## Examples from the [Vue 3 Essentials Tutorial](https://staging.vuejs.org/tutorial/)

### Declarative Rendering

[Guide 🏹](https://staging.vuejs.org/guide/essentials/reactivity-fundamentals.html)

#### Options

```js
<script>
export default {
  data() {
    return {
      message: 'Hi Earthlings!'
    }
  }
}
</script>

<template>
  <h1>{{ message.split('').reverse().join('') }}</h1>
</template
```

#### Composition

```js
<script setup>
import { ref } from 'vue'

const message = ref('Hi Earthlings!')
</script>

<template>
  <h1>{{ message.split('').reverse().join('') }}</h1>
</template>
```

### Attribute Bindings

[Guide 🏹](https://staging.vuejs.org/guide/essentials/template-syntax.html)

#### Options

```js
<script>
export default {
  data() {
    return {
      titleClass: 'brand'
    }
  }
}
</script>

<template>
  <h1 :class="titleClass">Sionnach Solutions</h1>
</template>

<style>
.brand {
  color: red;
}
</style>
```

#### Composition

```js
<script setup>
import { ref } from 'vue'

const titleClass = ref('brand')
</script>

<template>
  <h1 :class="titleClass">Sionnach Solutions</h1>
</template>

<style>
.brand {
  color: red;
}
</style>
```

### Event Listeners

[Guide 🏹](https://staging.vuejs.org/guide/essentials/event-handling.html)

#### Options

```js
<script>
export default {
  data() {
    return {
      count: 0
    }
  },
  methods: {
    inc() {
      this.count++
    }
  }
}
</script>

<template>
  <button @click="inc">{{ count }}</button>
</template>

#### Composition

```js
<script setup>
import { ref } from 'vue'

const count = ref(0)

function inc() {
  count.value++
}
</script>

<template>
  <button @click="inc">{{ count }}</button>
</template>
```

### Form Bindings

[Guide 🏹](https://staging.vuejs.org/guide/essentials/forms.html)

#### Options

```js
<script>
export default {
  data() {
    return {
      text: ''
    }
  }
}
</script>

<template>
  <input v-model="text" placeholder="Enter text">
  <p>{{ text }}</p>
</template>
```

#### Composition

```js
<script setup>
import { ref } from 'vue'

const text = ref('')
</script>

<template>
  <input v-model="text" placeholder="Enter text">
  <p>{{ text }}</p>
</template>
```

### Conditional Rendering

[Guide 🏹](https://staging.vuejs.org/guide/essentials/conditional.html)

#### Options

```js
<script>
export default {
  data() {
    return {
      show: true
    }
  },
  methods: {
    toggle() {
      this.show = !this.show
    }
  }
}
</script>

<template>
  <button @click="toggle">toggle</button>
  <h1 v-if="show">Sionnach Solutions is awesome! 🦊</h1>
  <h1 v-else>Sionnach Buí is even more awesome! 🦊🐈</h1>
</template>
```

#### Composition

```js
<script setup>
import { ref } from 'vue'

const show = ref(true)

function toggle() {
  show.value = !show.value
}
</script>

<template>
  <button @click="toggle">toggle</button>
  <h1 v-if="show">Sionnach Solutions is awesome! 🦊</h1>
  <h1 v-else>Sionnach Buí is even more awesome! 🦊🐈</h1>
</template>
```

### List Rendering

[Guide 🏹](https://staging.vuejs.org/guide/essentials/list.html)

#### Options

```js
<script>
// give each todo a unique id
let id = 0

export default {
  data() {
    return {
      newTodo: '',
      todo: [
        { id: id++, text: 'Yes' },
        { id: id++, text: 'No' },
        { id: id++, text: 'Maybe' }
      ]
    }
  },
  methods: {
    addTodo() {
      this.todos.push({ id: id++, text: this.newTodo })
      this.newTodo = ''
    },
    removeTodo(todo) {
      this.todos = this.todos.filter((t) => t !== todo)
    }
  }
}
</script>

<template>
  <input v-model="newTodo" @keyup.enter="addTodo">
  <button @click="addTodo">Add Todo</button>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>
```

#### Composition

```js
<script setup>
import { ref } from 'vue'

// give each todo a unique id
let id = 0

const newTodo = ref('')
const todos = ref([
  { id: id++, text: 'Yes' },
  { id: id++, text: 'No' },
  { id: id++, text: 'Maybe' }
])

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <input v-model="newTodo" @keyup.enter="addTodo">
  <button @click="addTodo">Add Todo</button>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>
```

### Computed Property

[Guide 🏹](https://staging.vuejs.org/guide/essentials/computed.html)

#### Options

```js
<script>
let id = 0

export default {
  data() {
    return {
      newTodo: '',
      hideCompleted: false,
      todos: [
        { id: id++, text: 'Yes', done: false },
        { id: id++, text: 'No', done: false },
        { id: id++, text: 'Maybe', done: false }
      ]
    }
  },
  computed: {
    filteredTodos() {
      return this.hideCompleted
        ? this.todos.filter((t) => !t.done)
        : this.todos
    }
  },
  methods: {
    addTodo() {
      this.todos.push({ id: id++, text: this.newTodo, done: false })
      this.newTodo = ''
    },
    removeTodo(todo) {
      this.todos = this.todos.filter((t => t !== todo)
    }
  }
}
</script>

<template>
  <input v-model="newTodo" @keyup.enter="addTodo" />
  <button @click="addTodo">Add Todo</button>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done" />
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>
```

#### Composition

```js
<script setup>
import { ref, computed } from 'vue'

let id = 0

const newTodo = ref('')
const hideCompleted = ref(false)
const todos = ref([
  { id: id++, text: 'Yes', done: false },
  { id: id++, text: 'No', done: false },
  { id: id++, text: 'Maybe', done: false }
])

const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <input v-model="newTodo" @keyup.enter="addTodo" />
  <button @click="addTodo">Add Todo</button>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done" />
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>
```

### Lifecycle and Template Refs

[Guide 🏹](https://staging.vuejs.org/guide/essentials/lifecycle.html)

![Instance lifecycle](https://staging.vuejs.org/assets/lifecycle.cec11dcc.png)

#### Options

```js
<script>
export default {
  mounted() {
    this.$refs.p.textContent = '🏔'
  }
}
</script>

<template>
  <p ref="p">🧗</p>
</template>
```

#### Composition

```js
<script setup>
import { ref, onMounted } from 'vue'

const p = ref(null)

onMounted(() => {
  p.value.textContent = '🏔'
})
</script>

<template>
  <p ref="p">🧗</p>
</template>
```

### Watchers

[Guide 🏹](https://staging.vuejs.org/guide/essentials/watchers.html)

#### Options

```js
<script>
export default {
  data() {
    return {
      count: 1,
      randomUser: null
    }
  },
  methods: {
    async fetchRandomUser() {
      this.randomUser = null
      const res = await fetch(
        `https://jsonplaceholder.typicode.com/users/${
        	Math.floor(Math.random() * 9) + 1
        }`
      )
      this.randomUser = await res.json()
    }
  },
  mounted() {
    this.fetchRandomUser()
  },
  watch: {
    count() {
      this.fetchRandomUser()
    }
  }
}
</script>

<template>
  <p>Query Count: {{ count }}</p>
  <button @click="count++">Fetch Random User</button>
  <p v-if="!randomUser">Fetching Random User...</p>
  <pre v-else>{{ randomUser }}</pre>
</template>
```

#### Composition

```js
<script setup>
import { ref, watch } from 'vue'

const count = ref(1)
const randomUser = ref(null)

async function fetchRandomUser() {
  randomUser.value = null
  const res = await fetch(
        `https://jsonplaceholder.typicode.com/users/${
        	Math.floor(Math.random() * 9) + 1
        }`
      )
  randomUser.value = await res.json()
}

fetchRandomUser()

watch(count, fetchRandomUser)
</script>

<template>
  <p>Query Count: {{ count }}</p>
  <button @click="count++">Fetch Random User</button>
  <p v-if="!randomUser">Fetching Random User...</p>
  <pre v-else>{{ randomUser }}</pre>
</template>
```

### Components

[Basics Guide 🏹](https://staging.vuejs.org/guide/essentials/component-basics.html)

```js
// AlienComponent.vue
<template>
  <h2>Congratulations! It's an alien! 👽</h2>
</template>
```

#### Options

```js
<script>
import AlienChild from './AlienComponent.vue'

export default {
  components: {
    AlienChild
  }
}
</script>

<template>
  <AlienChild />
</template>
```

#### Composition

```js
<script setup>
import AlienChild from './AlienComponent.vue'
</script>

<template>
  <AlienChild />
</template>
```

### Props

[Guide 🏹](https://staging.vuejs.org/guide/components/props.html)

#### Options

```js
// AlienComponent.vue
<script>
export default {
  props: {
    msg: String
  }
}
</script>

<template>
  <h2>{{ msg || 'Mommy?' }}</h2>
</template>
```

```js
<script>
import AlienChild from './AlienComponent.vue'

export default {
  components: {
    AlienChild 
  },
  data() {
    return {
      greeting: 'Mommy loves you!'
    }
  }
}
</script>

<template>
  <AlienChild :msg="greeting" />
</template>
```

#### Composition

```js
// AlienComponent.vue
<script setup>
const props = defineProps({
  msg: String
})
</script>

<template>
  <h2>{{ msg || 'Mommy?' }}</h2>
</template>
```

```js
<script setup>
import { ref } from 'vue'
import AlienChild from './AlienComponent.vue'

const greeting = ref('Mommy loves you!')
</script>

<template>
  <AlienChild  :msg="greeting" />
</template>
```

### Emits (Emitting and Listening to Events)

[Guide 🏹](https://staging.vuejs.org/guide/components/events.html)

#### Options

```js
// AlienComponent.vue
<script>
export default {
  emits: ['response'],
  created() {
    this.$emit('response', 'ET Phone Home!')
  }
}
</script>

<template>
  <h2>👽</h2>
</template>
```

```js
<script>
import AlienChild from './AlienComponent.vue'

export default {
  components: {
    AlienChild
  },
  data() {
    return {
      phoneCall: 'No call yet 😱'
    }
  }
}
</script>

<template>
  <AlienChild @response="(msg) => phoneCall = msg" />
  <p>{{ phoneCall }}</p>
</template>
```

#### Composition

```js
// AlienComponent.vue
<script setup>
const emit = defineEmits(['response'])

emit('response', 'ET Phone Home!')
</script>

<template>
  <h2>👽</h2>
</template>
```

```js
<script setup>
import { ref } from 'vue'
import AlienChild from './AlienComponent.vue'

const phoneCall = ref('No call yet 😱')
</script>

<template>
  <AlienChild @response="(msg) => phoneCall = msg" />
  <p>{{ phoneCall }}</p>
</template>
```

### Slots

[Guide 🏹](https://staging.vuejs.org/guide/components/slots.html)

```js
// AlienComponent.vue
<template>
  <slot>Fallback content</slot>
</template>
```

#### Options

```js
<script>
import AlienChild from './AlienComponent.vue'

export default {
  components: {
    AlienChild
  },
  data() {
    return {
      msg: '👽'
    }
  }
}
</script>

<template>
  <AlienChild>{{ msg }}</AlienChild>
</template>
```

#### Composition

```js
<script setup>
import { ref } from 'vue'
import AlienChild from './AlienComponent.vue'

const msg = ref('👽')
</script>

<template>
  <AlienChild>{{ msg }}</AlienChild>
</template>
```

[Tutorial Source](https://staging.vuejs.org/tutorial/)
