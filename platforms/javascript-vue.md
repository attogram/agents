# Working with Vue.js

This document provides guidelines and best practices for AI agents working on Vue.js projects. Vue is a progressive JavaScript framework for building user interfaces. The focus here is on **Vue 3** and the **Composition API**.

## 1. Core Concepts

- **Progressive Framework**: Vue is designed to be incrementally adoptable. The core library is focused on the view layer only, but it can be easily integrated with other libraries or existing projects.
- **Single-File Components (SFCs)**: The standard way to write Vue components is in `.vue` files. These files encapsulate the component's template, logic, and styles in one place.

  ```vue
  <template>
    <div class="greeting">{{ msg }}</div>
  </template>

  <script setup>
  import { ref } from "vue";

  const msg = ref("Hello World!");
  </script>

  <style scoped>
  .greeting {
    color: red;
  }
  </style>
  ```

- **Template Syntax**: Vue uses an HTML-based template syntax that allows you to declaratively bind the rendered DOM to the underlying component instance's data.
  - **Directives**: Special attributes with the `v-` prefix (e.g., `v-if` for conditional rendering, `v-for` for list rendering, `v-bind` for binding attributes, `v-on` for listening to events).
  - **Interpolation**: Use double curly braces `{{ }}` for text interpolation.

## 2. The Composition API

The Composition API is the recommended way to write components in Vue 3. It allows for better code organization and reuse by grouping logic by feature instead of by options (data, methods, etc.).

- **`setup` script**: The `<script setup>` block is compile-time syntactic sugar for using the Composition API inside SFCs. It's the most straightforward way to write Composition API components.
- **Reactivity**:
  - **`ref`**: Takes an inner value and returns a reactive and mutable ref object. To access the value, you need to use `.value`.
    ```javascript
    import { ref } from "vue";
    const count = ref(0);
    console.log(count.value); // 0
    ```
  - **`reactive`**: Returns a reactive proxy of an object. It is deeply reactive.
    ```javascript
    import { reactive } from "vue";
    const state = reactive({ count: 0 });
    ```
- **Computed Properties**: `computed` is used to declare a value that depends on other reactive state. It will be automatically updated when its dependencies change.
  ```javascript
  import { ref, computed } from "vue";
  const count = ref(0);
  const double = computed(() => count.value * 2);
  ```
- **Lifecycle Hooks**: You can register lifecycle hooks by importing them from `vue`. The most common is `onMounted`.
  ```javascript
  import { onMounted } from "vue";
  onMounted(() => {
    console.log("Component has been mounted.");
  });
  ```

## 3. Component Communication

- **Props**: Data is passed from a parent to a child component via props. In `<script setup>`, props are defined with the `defineProps` macro.
  ```javascript
  // ChildComponent.vue
  const props = defineProps({
    message: String,
  });
  ```
- **Events**: A child component can emit an event to its parent using the `defineEmits` macro and the returned `emit` function.
  ```javascript
  // ChildComponent.vue
  const emit = defineEmits(["response"]);
  emit("response", "hello from child");
  ```

## 4. Development Environment

- **Vite**: The official and recommended build tool for modern Vue projects. It provides a fast development server and an optimized build process.
  ```bash
  npm create vite@latest my-vue-app -- --template vue
  ```
- **Vue CLI**: The traditional tool for creating Vue projects, built on top of webpack. While still supported, Vite is recommended for new projects.
