<template>
  <div class="grid-container">
    <div class="left">
      <slot name="left"></slot>
    </div>
    <div class="title">
      <slot name="title"></slot>
    </div>
    <div class="actions">
      <div class="actionSlot" :key="index" v-for="(slot, index) in actionSlots">
        <slot :name="slot"></slot>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "oc-app-top-bar",
  status: "prototype",
  release: "0.0.1",
  computed: {
    actionSlots() {
      let filteredSlots = Object.keys(this.$slots).filter(s => {
        return s.startsWith("action_")
      })
      return filteredSlots.reverse()
    },
  },
}
</script>
<style lang="scss" scoped>
.grid-container {
  background: #e3e3e3;
  width: 100%;
  display: grid;
  grid-template-columns: auto auto 1fr;
  grid-template-rows: 1fr;
  grid-template-areas: "info title actions";
}

.actionSlot {
  float: right;
}

.left {
  min-width: 25vw;
  grid-area: info;
  .icon {
    position: absolute;
    margin: 0.5em 1em;
  }
}

.title {
  max-width: 30vw;
  grid-area: title;
}

.actions {
  float: right;
  margin-right: 0.5em;
  grid-area: actions;
  .button {
    margin-top: 1.2em;
  }
}
</style>

<docs>
  ```jsx
  <OcAppTopBar>
    <div slot="left">
      <oc-icon name="account_circle" size="large" />
    </div>
    <div slot="title">
      <h4>OcAppTopBar Demo</h4>
    </div>
    <div slot="action_close">
      <oc-button>
        <oc-icon name="close" />
      </oc-button>
    </div>
  </OcAppTopBar>
  ```
</docs>
