<template>
  <div class="delivery-record">
    <div class="status">
      <div class="deliverystatus" :style="{'background-color': deliverystatusType.find(({val}) => val === deliverystatus).color}">{{ deliverystatusType.find(({val}) => val === deliverystatus).lab}}</div>
      <input type="checkbox" class="switch">
    </div>
    <div class="content">
    <span class="addsname"><strong>{{ addsname }}</strong></span>
    <div class="text">
      <div class="left">
        <span class="mstyle">预算金额</span>
        <span class="number"><strong>{{ budgetmoney }} </strong><span class="tstyle">元</span></span>
      </div>
      <div class="right">
        <span class="mstyle">预计展示次数</span>
        <span class="number"><strong>{{ showtimes }} </strong><span class="tstyle">次</span></span>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DeliveryRecord',
  props: {
    deliverystatus: {
      type: Number,
      default: 0
    },
    addsname: {
      type: String,
      default: '这是一个广告名称'
    },
    budgetmoney: {
      type: Number,
      default: 1000
    },
    showtimes: {
      type: Number,
      default: 1000
    }
  },
  data() {
    return {
      deliverystatusType: [
        { lab: '投放中', val: 0, color: '#E4FFD5' },
        { lab: '审核中', val: 1, color: '#F2CEE6' },
        { lab: '暂停中', val: 2, color: '#d8d8d8' }
      ]
    }
  }
}
</script>
<style lang="scss">
.delivery-record{
  width: 90%;
  background-color: white;
  border-radius: 7%;
  padding-bottom: 0.3rem;
  .status{
    font-size: 0.3rem;
    height: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 0.02rem solid lightgray;
    margin-bottom: 0.3rem;
    .deliverystatus{
      background-color: rgb(228,255,207);
      text-align: center;
      border-radius: 0 0.5rem 0.5rem 0;
      width: 1.2rem;
      height: 0.5rem;
      line-height: 0.5rem;
    }
    /* Switch开关样式 */
 /* 必须是input为 checkbox class 添加 switch 才能实现以下效果 */
   input[type='checkbox'].switch{
    outline: none;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    position: relative;
    width: 0.8rem;
    height: 0.4rem;
    background: #ccc;
    border-radius: 0.2rem;
    transition: border-color .3s, background-color .3s;
}
  input[type='checkbox'].switch::after {
    content: '';
    display: inline-block;
    width: 0.32rem;
    height:0.32rem;
    border-radius: 50%;
    background: #fff;
    box-shadow: 0, 0, 0.02rem, #999;
    transition:.4s;
    top: 0.02rem;
    position: absolute;
    left: 0.02rem;
}
  input[type='checkbox'].switch:checked {
    background: #4e6bff;
}
/* 当input[type=checkbox]被选中时：伪元素显示下面样式 位置发生变化 */
  input[type='checkbox'].switch:checked::after {
    content: '';
    position: absolute;
    left: 55%;
    top: 0.02rem;
}
  }
  .content{
    padding-left: 0.3rem;
  .addsname{
    font-size: 0.5rem;
  }
  .text,.left,.right{
    display: flex;
    .left,.right{
      flex-direction: column;
      width: 3rem;
      margin-top: 0.3rem;
      .number{
        font-size: 0.5rem;
        padding-right: 0.2rem;
      }
      .tstyle{
        font-size: 0.3rem;
      }
      .mstyle{
        font-size: 0.35rem;
        padding: 0.2rem 0 0.2rem 0;
        color: #626367;
      }
    }
  }
  }
}
</style>
