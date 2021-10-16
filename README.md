# modal-project

## Notes

### Template Refs

Template Refs give us the ability to place a handle on DOM elements. Similar to jQuery querying selectors utilizing Template Refs gives us a similar ability.

**Example**

## Template Refs

<details>
<summary>Template Refs</summary>

```js
<input type='text' ref='name'>
<button @click='handleClick'>Click Me </button>
```

This ref='name' allows us to utilize this ref to add event listeners and handle certain actions on this element.

**example**

```js
export default {
    name: 'App',
        data() {
            return {
                title: 'My Vue App',
            };
        },
        methods:
            handleClick() {
                console.log(this.$refs.name);
                this.$refs.name.classList.add('active')
                this.$refs.name.focus()
            },
}
```

</details>


<details>
<summary>Modal App.Vue</summary>

```js
App.vue
<template>
  <h1>{{ title }}</h1>
  <Modal />
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My First Vue Application",
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>

```

```js
Modal.vue
<template>
  <div class="backdrop">
    <div class="modal">
      <p>Modal Content</p>
    </div>
  </div>
</template>


<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
</style>
```

</details>


<details>
<summary> Scoped Styles </summary>

```js
<style scoped> 
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
```

<p>This will only apply these styles to the current template or component based on the scope.  This can be load heavy and cause performance issues if done at a large scale. Another option is to specify the class ahead of any main elements.  So in this case if we have an h1, we can apply the .modal class to the h1 and the style will only apply to that h1 element of the Modal component.</p>
</details>


<details>
<summary>Props</summary>
<p>We can pass props from a parent component to a child component. Makes our components more reusable.  Can be passed props from each parent component where it is used.  If we have multiple components using the same data, we only have to define the data in one single component.</p>

```js
  <Modal header="Sign up for the Team!"/>
  ```

<p>We add an attribute to our Modal component inside the App.vue file so that we can tell the component what Prop we are actually wanting to pass to the component in this case a prop called header. Then inside of our Modal.vue component file we can do the following below our template: </p>

```js
<script>
export default {
  props: ['header']
}
</script>
```
<p>This tells our Modal component to accept the props coming from the Parent and what props we are accepting, in our case the 'header' prop that we passed inside App.vue.
</p>
</details>


<details>
<summary>Emitting custom Events</summary>

<p>Modal.vue</p>

```js
  <div class="backdrop" @click="closeModal">
```

```js
  methods: {
    closeModal() {
      this.$emit('close')
    }
```
<p>App.vue</p>

```js
<template>
  <h1>{{ title }}</h1>
  <p>Welcome to our Vue Application</p>
<div v-if="showModal">
    <Modal :header="header" :text="text" theme="sale" @close="toggleModal" />
</div>
<button @click='toggleModal'>Open Modal</button>
</template>




<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My First Vue Application",
      header: "Sign up for the Team!",
      text: 'Join the Junior Developer Group!',
      showModal: false
    };
  },
  methods: {
    toggleModal() {
      this.showModal=!this.showModal
    }
  },
};
</script>

```

</details>

<details>
<summary>How to Setup and Run</summary>
## Project setup

```
yarn install
```

### Compiles and hot-reloads for development

```
yarn serve
```

### Compiles and minifies for production

```
yarn build
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

</details>
