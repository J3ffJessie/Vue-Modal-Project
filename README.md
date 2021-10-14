# modal-project

## Notes

### Template Refs

Template Refs give us the ability to place a handle on DOM elements. Similar to jQuery querying selectors utilizing Template Refs gives us a similar ability.

**Example**

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
