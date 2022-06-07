<template>
  <header class="header">
    <h1>todos</h1>
    <input id="toggle-all" class="toggle-all" type="checkbox" v-model="isAll" />
    <label for="toggle-all"></label>
    <input
      class="new-todo"
      placeholder="输入任务名称-回车确认"
      autofocus
      v-model="task"
      @keydown.enter="downFn"
    />
  </header>
</template>

<script>
export default {
  data() {
    return {
      task: '',
    }
  },
  props: ['arr'],
  methods: {
    downFn() {
      this.$emit('create', this.task)
      this.task = ''
    },
  },
  computed: {
    isAll: {
      set(checked) {
        this.arr.forEach((obj) => {
          obj.isDone = checked
        })
      },
      get() {
        return (
          this.arr.length !== 0 &&
          this.arr.every((obj) => {
            return obj.isDone === true
          })
        )
      },
    },
  },
}
</script>
