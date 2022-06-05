<template>
  <footer class="footer">
    <span class="todo-count"
      >剩余<strong>{{ count }}</strong></span
    >
    <ul class="filters" @click="fn">
      <li>
        <a
          :class="{ selected: isSel === 'All' }"
          href="javascript:;"
          @click="isSel = 'All'"
          >全部</a
        >
      </li>
      <li>
        <a
          :class="{ selected: isSel === 'no' }"
          href="javascript:;"
          @click="isSel = 'no'"
          >未完成</a
        >
      </li>
      <li>
        <a
          :class="{ selected: isSel === 'yes' }"
          href="javascript:;"
          @click="isSel = 'yes'"
          >已完成</a
        >
      </li>
    </ul>
    <button class="clear-completed" @click="clearFn">清除已完成</button>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      isSel: 'All', //All为全显示，yes为已完成，no为未完成
    }
  },
  props: ['farr'],
  computed: {
    count() {
      return this.farr.length
    },
  },
  methods: {
    fn(){
      this.$emit('changeType',this.isSel)
    },
    clearFn(){
      this.$emit('clear')
    }
  }
}
</script>
