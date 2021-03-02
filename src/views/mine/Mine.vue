<template>
<div class="wrapper">
    <!-- 头部 -->
    <div class="header">
        <img :src="img">
        <div class="h-right">
            <span class="company">{{info.company}}</span>
            <span>{{info.phone}}</span>
        </div>
    </div>
    <!-- 余额 -->
    <div class="info">
        <div class="detailinfo">
            <div class="leftmoney">
                <span class="mstyle">账户余额</span>
                <span class="lmoneynumber"><strong>{{info.leftmoney}}</strong></span>
            </div>
            <div class="sendmoney">
                <span class="mstyle">赠送金额</span>
                <span class="smoneynumber"><strong>{{info.sendmoney}}</strong></span>
            </div>
        </div>
        <div class="message">
            <span>优惠大放送，充值返好礼</span>
            <button>立即充值</button>
        </div>
    </div>
    <!-- 表单信息 -->
    <div class="form">
        <div class="form-item">
            <span>投放记录</span>
            <img src="../../assets/images/mine/right-arrow.svg">
        </div>
         <div class="form-item">
            <span>充值记录</span>
            <img src="../../assets/images/mine/right-arrow.svg">
        </div>
         <div class="form-item">
            <span>修改手机号</span>
            <img src="../../assets/images/mine/right-arrow.svg">
        </div>
         <div class="form-item">
            <span>联系客服</span>
            <img src="../../assets/images/mine/right-arrow.svg">
        </div>
         <div class="form-item">
            <span>用户协议</span>
            <img src="../../assets/images/mine/right-arrow.svg">
        </div>
         <div class="form-item">
            <span>版本信息：2.0.1</span>
            <img src="../../assets/images/mine/right-arrow.svg">
        </div>
    </div>
</div>
</template>

<script>
import img from '../../assets/images/mine/img.jpg'
export default {
  name: 'Mine',
  data() {
    return {
      img,
      info: {
        img: 'img',
        company: '江苏布点网络科技有限公司',
        phone: '13567890987',
        leftmoney: '29982.06',
        sendmoney: '99'
      }
    }
  }
}
</script>

<style lang='scss'>
.wrapper{
  background-color: rgb(246,247,249);
  // 头部
  .header{
    color: white;
    padding: 0.7rem;
    height: 2.5rem;
    background-color: rgb(56,96,254);
    display: flex;
    img{
      width: 1.3rem;
      height: 1.3rem;
      border-radius: 100%;
      }
    .h-right{
      display: flex;
      flex-direction: column;
      padding-left: 0.2rem;
      .company{
        font-size: 0.4rem;
        padding-bottom: 0.2rem;
        }
    }
  }
   // 账户余额
  .info{
    background-color: white;
    width: 90%;
    margin: 0 auto;
    position: absolute;
    top: 3rem;
    left: 0;
    right: 0;
    border-radius: 0.3rem;
    padding-bottom: 0.2rem;
    .detailinfo{
        padding: 0.5rem 0.5rem 0.3rem 0.5rem;
        box-sizing: border-box;
        width: 100%;
        display: flex;
        border-bottom: 0.01rem solid lightgrey;
        .leftmoney,.sendmoney{
            display: flex;
            flex-direction: column;
        }
        .leftmoney{
            margin: 0 1.5rem 0.3rem 0;
            .lmoneynumber{
                font-size: 0.5rem;
            }
        }
        .smoneynumber{
            color: rgb(237,149,117);
            font-size: 0.5rem;
        }
        .mstyle{
            color: rgb(112,112,112);
            padding-bottom: 0.3rem;
        }
    }
    .message{
        padding: 0.2rem 0.5rem 0 0.5rem;
        align-items: center;
        display: flex;
        justify-content: space-between;
        span{
            color: rgb(80,121,254);
        }
        button{
            background: rgb(80,121,254);
            font-size: 0.3rem;
            color:  white;
            border-radius: 0.1rem;
            border: 0;
            outline: none;
        }
    }
  }
  // 表单
  .form{
      width: 90%;
      margin: 2.5rem auto;
      .form-item{
          display: flex;
          justify-content: space-between;
          font-size: 0.4rem;
          background-color: white;
          margin: 0.3rem 0;
          padding: 0.25rem;
          border-radius: 0.2rem;
          img{
              width: 0.4rem;
              height: 0.4rem;
          }
      }
  }
}

</style>
