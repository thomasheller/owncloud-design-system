<template>
  <ul class="uk-breadcrumb">
    <li v-for="item in items" :class="{ 'uk-disabled' : item.disabled }">
      <a :href="item.to">{{ item.text }}</a>
    </li>
  </ul>
</template>

<script>
/**
 * The breadcrumbs component consists of links, which are aligned side by side
 * and separated by a divider.
 */
export default {
  name: "oc-breadcrumbs",
  status: "review",
  release: "1.0.0",
  props: {
    /**
     * The links to be displayed (as plain objects).
     */
    items: {
      required: true,
      type: Array,
    },
    /**
     * The divider character/string separating the links.
     */
    divider: {
      type: String,
      default: ">",
    },
  },
}
</script>

<style scoped>
.uk-breadcrumb>:nth-child(n+2):not(.uk-first-column)::before {
    content: ">";
    margin: 0 10px;
}
</style>

<docs>
  ```jsx
  <div>
    <oc-breadcrumbs :items="[
      {text: 'Home', to: '/'},
      {text: 'Users', to: '/users'},
      {text: 'A', disabled: true},
      {text: 'Alice', to: '/users/alice'},
    ]" divider=">"></oc-breadcrumbs>
  </div>
  ```
</docs>
