<template>
  <div class="wrapper">
    <!-- 头部 -->
    <div class="header">
      <div class="company">
        <img class="account" src="../../assets/images/home/account.svg">
        <span>{{info.company}}</span>
        <img class="arrow" src="../../assets/images/home/company-down-arrow.svg">
      </div>
      <div class="money">
        <span class="text">账户余额(元)</span>
        <span class="left-money"><strong>{{info.leftmoney}}</strong></span>
      </div>
      <div class="edit">
        <span class="text">点击充值</span>
        <img src="../../assets/images/home/edit.svg">
      </div>
    </div>
    <!-- 数据看板 -->
    <div class="data-area">
      <div class="data-head">
        <img class="data" src="../../assets/images/home/data.svg">
        <span class="data-text"><strong>数据看板</strong></span>
        <div class="date">
          <span>今日</span>
          <img class="down" src="../../assets/images/home/down-arrow.svg">
        </div>
      </div>
      <div class="data-content">
        <div class="common">
          <span class="gray">消耗金额(元)</span>
          <span class="number"><strong>500.00</strong></span>
        </div>
        <div class="common">
          <span class="gray">展示次数(次)</span>
          <span class="number"><strong>1200</strong></span>
        </div>
        <div class="common">
          <span class="gray">投放中广告(个)</span>
          <span class="number"><strong>16</strong></span>
        </div>
      </div>
      <div class="foot">
        <div class="system">系统</div>
        <span>因系统升级，广告通服务将于3月...</span>
      </div>
    </div>
    <!-- 投放记录标题 -->
    <div class="history">
      <div class="left">
        <div class="style-div" />
        <span><strong>投放记录</strong></span>
      </div>
      <div class="right">
        <span>更多</span>
        <img src="../../assets/images/home/right-arrow.svg">
      </div>
    </div>
    <!-- 投放组件 -->
    <delivery-record class="delivery-record" :deliverystatus='deliverystatus'></delivery-record>
  </div>
</template>

<script>
import DeliveryRecord from '../../components/common/DeliveryRecord.vue'
export default {
  name: 'Home',
  components: {
    DeliveryRecord
  },
  data() {
    return {
      info: {
        company: '江苏布点网络科技有限公司',
        leftmoney: 5000
      },
      deliverystatus: 0
    }
  }
}
</script>

<style lang="scss">
$main-color:#4e6bff;
.wrapper{
  background-color: rgb(246,247,249);
  // height: 15rem;
}
// 头部
.header{
    height: 7rem;
    background-color: $main-color;
    padding: 0.3rem;
    color: white;
    // position: relative;
    .text{
        color: rgb(138, 167, 251);
    }
  .company{
    padding: 0.4rem 0;
    .account{
    width: 0.5rem;
    height: 0.5rem;
    }
    .arrow{
    width: 0.3rem;
    height: 0.3rem;
    }
    span{
    padding: 0 0.3rem;
    font-size: 0.45rem;
    }
}
  .money{
    display: flex;
    flex-direction: column;
      .left-money{
        padding: 0.3rem 0;
        font-size: 0.55rem;
    }
}
  .edit{
    img{
      width: 0.33rem;
      height: 0.33rem;
    }
    span{
        padding-right: 0.3rem;
    }
  }
}
// 数据看板
.data-area{
    width: 90%;
    background-color: white;
    position: absolute;
    top: 5rem;
    left: 0;
    right: 0;
    margin: 0 auto;
    border-radius: 5%;
    padding: 0.4rem;
    box-sizing: border-box;
  .data-head{
    font-size: 0.3rem;
    height: 0.8rem;
    line-height: 0.8rem;
    display: flex;
      .data-text{
      padding: 0 3rem 0 0.3rem;
      font-size: 0.4rem;
    }
    .data{
      width: 0.45rem;
      height: 0.45rem;
      padding-top: 0.14rem;
    }
    .date{
        width: 2.5rem;
        text-align: center;
        background-color: rgb(239, 244, 250);
        border-radius: 7%;
        .down{
        width: 0.4rem;
        height: 0.4rem;
    }
    }
  }
  .data-content{
    padding: 0.3rem 0;
    display: flex;
    justify-content: space-around;
    .common{
      width: 2.5rem;
      background-color: rgb(248, 249, 253);
      border-radius: 3%;
      height: 2.2rem;
      display: flex;
      flex-direction: column;
      padding: 0.4rem 0 0.3rem 0.2rem;
      box-sizing: border-box;
      .gray{
        color: rgb(98, 99, 103);
      }
      .number{
        padding-top: 0.3rem;
        font-size: 0.42rem;
      }
    }
  }
  .foot{
  font-size: 0.3rem;
  height: 1.2rem;
  background-color: rgb(239, 243, 255);
  display: flex;
  line-height: 1rem;
  border-radius: 6%;
  position: relative;
  .system{
    width: 1.2rem;
    height: 0.7rem;
    line-height: 0.7rem;
    color: white;
    border-radius: 10%;
    text-align: center;
    background-color: $main-color;
    margin-right: 0.3rem;
    position: absolute;
    top: 0;
    bottom: 0;
    margin: auto 0.2rem;
  }
  span{
    margin-left: 1.6rem;
    line-height: 1.2rem;
  }
}
}
// 投放记录
.history{
  width: 90%;
  padding-top: 3.3rem;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  .left{
    font-size: 0.5rem;
    line-height: 0.45rem;
    display: flex;
    .style-div{
    width: 0.1rem;
    height: 85%;
    margin-right: 0.2rem;
    border-radius: 15%;
    background-color: $main-color;
  }
  }
  .right{
    color: #626367;
    font-size: 0.3rem;
    img{
      width: 0.4rem;
      height: 0.4rem;
    }
  }
}
.delivery-record{
  margin: 0.5rem auto;
}
</style>
