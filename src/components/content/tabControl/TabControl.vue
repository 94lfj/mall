<template>
  <div class="tabcontrol">
    <div v-for="(item,index) in titles" :key="item" 
        class="tab-control-item"
        :class="{active: index === currenIndex}"
        @click="itemClick(index)">
      <span>{{item}}</span>
    </div>
  </div>
</template>
<script>
export default {
  name:"TabControl",
  props: {
    titles: {
      type: Array,
      default() {
        return [];
      }
    }
  },
  data() {
    return {
      currenIndex:0
    }
  },
  methods: {
    itemClick(index) {
      this.currenIndex = index;
    }
  }
}
</script>
<style scoped>
.tabcontrol{
  display: flex;
  text-align: center;
  font-size: 15px;
  height: 40px;
  line-height: 40px;
  background: #fff;
}
.tabcontrol .tab-control-item {
  flex: 1;
}
.tab-control-item span{
  padding: 5px;
}
.active {
  color: var(--color-high-text);
}
.active span {
  border-bottom: 3px solid var(--color-high-text);
}
</style>