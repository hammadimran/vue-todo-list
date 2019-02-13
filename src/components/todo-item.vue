<template>
  <transition name="el-zoom-in-top">
  <li>

    <el-button type="success" icon="el-icon-check" circle class="btn"
               v-bind:class="{ done: this.completed }"
               v-on:click="$emit('toggle')"></el-button>
    <el-button type="danger" icon="el-icon-delete" circle class="btn"
               v-bind:class="{ delete: this.completed }"
               v-on:click="$emit('delete')"></el-button>
    <span v-bind:class="{ completed: this.completed }">
      <div>{{this.title}}</div>
      <div>{{this.date}}</div>
    </span>
  </li>
  </transition>
</template>

<script>
    export default {
        name: "todo-item",
      props: ['title', 'completed', 'date'],
    }
</script>

<style scoped>

</style>
