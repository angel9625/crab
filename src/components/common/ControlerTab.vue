<template>
  <div class="controlertab">
            <ul class="status">
                <li :class="{active:index == currentindex}" v-for="(item,index) in status" :key="index" @click="itemClick(index,item)">{{item}}</li>
            </ul>
        </div>
</template>

<script>
export default {
  name: 'ControlerTab',
  props: {
    status: {
      type: Array,
      default() {
        return []
      }
    }
  },
  data() {
    return {
      currentindex: 0
    }
  },
  methods: {
    itemClick(index, item) {
      this.currentindex = index
      const param = {
        index: index,
        item: item
      }
      this.$emit('itemClick', param)
    }
  }
}
</script>

<style lang='scss'>
.controlertab{
  background-color: white;
  width: 100%;
  padding-bottom: 0.2rem;
  .status{
    width: 80%;
    display: flex;
    margin: 0 auto;
    justify-content: space-around;
    padding: 0;
    li{
      list-style: none;
      font-size: 0.4rem;
      color: #8d8c8c;
    }
    .active{
        color: rgb(82,102,194);
        border-bottom: 0.06rem solid rgb(82,102,194);
    }
    }
}
</style>
