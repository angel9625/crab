<template>
<div class="wrapper">
    <!-- 头部 -->
    <div class="header">
        <div class="search">
            <img src="../../assets/images/history/search.svg">
            <input type="text"  placeholder="请输入您要搜索的广告名称" placeholder-style="pclass">
        </div>
    </div>
    <!-- 选项卡 -->
    <controler-tab :status="tabs" @itemClick="itemClick"></controler-tab>
    <!-- 广告 -->
    <div>
        <delivery-record :deliverystatus="item" class="delivery-record" v-for="(item,index) in list" :key="index">{{item.lab}}</delivery-record>
    </div>
</div>
</template>

<script>
import ControlerTab from '../../components/common/ControlerTab.vue'
import DeliveryRecord from '../../components/common/DeliveryRecord.vue'
export default {
  components: { DeliveryRecord, ControlerTab },
  name: 'Home',
  data() {
    return {
      list: [0, 1, 2],
      list1: [1, 1, 1],
      list2: [2, 2, 2],
      list3: [0, 0, 0],
      // 装入需要的tab选项卡
      tabs: ['全部', '投放中', '审核中', '暂停中'],
      currentTab: 0
    }
  },
  methods: {
    itemClick(e) {
      //   console.log(e, 'e')
      this.currentTab = e.index
      this.getList(this.currentTab)
    },
    getList(e) {
      if (e === 1) {
        this.list = this.list3
      } else if (e === 2) {
        this.list = this.list1
      } else if (e === 3) {
        this.list = this.list2
      }
    }
  }
}
</script>

<style lang="scss">
.wrapper{
    background-color: rgb(246,247,249);
    .header{
        background-color: white;
        padding-bottom: 0.2rem;
        .search{
            position: relative;
            width: 90%;
            margin: 0.3rem auto;
            img{
                width: 0.5rem;
                height: 0.5rem;
                position: absolute;
                top: 0.2rem;
                left: 0.5rem;
            }
            input{
                width: 100%;
                border-radius: 0.6rem;
                border: 0.05rem solid rgb(80,102,178);
                outline: none;
                padding: 0.2rem 0 0.2rem 1.2rem;
                box-sizing: border-box;
                .pclass{
                    color: #8d8c8c;
                }
            }
        }
    }
    .delivery-record{
        margin: 0.3rem auto;
    }
}
</style>
