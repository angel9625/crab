<template>
  <div class="calendar_box">
    <div class="title" @click="show">弹出日历</div>
    <div v-show="isFlag" class="popup">
      <div class="calendar">
        <div class="calendar_title">日期选择
          <i class="iconfont icon-guanbi" @click="hide" />
        </div>
        <div class="year_month_box">
          <i class="iconfont icon-shangyiye" @click="pickPre(currentYear,currentMonth)" />
          <div class="year_month">{{ currentYear }}年{{ currentMonth }}月</div>
          <i class="iconfont icon-xiayiye" @click="pickNext(currentYear,currentMonth)" />
        </div>
        <div class="week">
          <span v-for="(item, index) in week" :key="index">{{ item }}</span>
        </div>
        <div class="date_num">
          <div v-for="(item, index) in days" :key="index" class="nums">
            <span v-if="item.day.getMonth()+1 != currentMonth" class="other-month">{{ item.day.getDate() }}</span>
            <span v-else>
              <span v-if="item.day.getFullYear() == new Date().getFullYear() && item.day.getMonth() == new Date().getMonth() && item.day.getDate() == new Date().getDate()" class="active">{{ item.day.getDate() }}</span>
              <span v-else>{{ item.day.getDate() }}</span>
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      week: ['日', '一', '二', '三', '四', '五', '六'],
      currentDay: 1,
      currentMonth: 1,
      currentYear: 2021,
      currentWeek: 1,
      days: [],
      isFlag: false
    }
  },
  created: function() {
    // 在vue初始化时调用
    this.initData(null)
  },
  methods: {
    show: function() {
      this.isFlag = true
    },
    hide: function() {
      this.isFlag = false
    },
    initData: function(cur) {
      // var leftcount = 0 // 存放剩余数量
      var date
      if (cur) {
        date = new Date(cur)
      } else {
        var now = new Date()
        var d = new Date(this.formatDate(now.getFullYear(), now.getMonth(), 1))
        d.setDate(35)
        date = new Date(this.formatDate(d.getFullYear(), d.getMonth() + 1, 1))
      }
      this.currentDay = date.getDate()
      this.currentYear = date.getFullYear()
      this.currentMonth = date.getMonth() + 1
      this.currentWeek = date.getDay() // 1...6,0
      if (this.currentWeek === 0) {
        this.currentWeek = 7
      }
      var str = this.formatDate(
        this.currentYear,
        this.currentMonth,
        this.currentDay
      )
      this.days.length = 0
      // 今天是周日，放在第一行第7个位置，前面6个
      // 初始化本周
      for (var i = this.currentWeek; i >= 0; i--) {
        var d2 = new Date(str)
        d2.setDate(d2.getDate() - i)
        var dayobjectSelf = {} // 用一个对象包装Date对象  以便为以后预定功能添加属性
        dayobjectSelf.day = d2
        this.days.push(dayobjectSelf) // 将日期放入data 中的days数组 供页面渲染使用
      }
      // 其他周
      for (var j = 1; j <= 35 - this.currentWeek; j++) {
        var d3 = new Date(str)
        d3.setDate(d3.getDate() + j)
        var dayobjectOther = {}
        dayobjectOther.day = d3
        this.days.push(dayobjectOther)
      }
    },
    pickPre: function(year, month) {
      // setDate(0); 上月最后一天
      // setDate(-1); 上月倒数第二天
      // setDate(dx) 参数dx为 上月最后一天的前后dx天
      var d = new Date(this.formatDate(year, month, 1))
      d.setDate(0)
      this.initData(this.formatDate(d.getFullYear(), d.getMonth() + 1, 1))
    },
    pickNext: function(year, month) {
      var d = new Date(this.formatDate(year, month, 1))
      d.setDate(35)
      this.initData(this.formatDate(d.getFullYear(), d.getMonth() + 1, 1))
    },
    // 返回 类似 2016-01-02 格式的字符串
    formatDate: function(year, month, day) {
      var y = year
      var m = month
      if (m < 10) m = '0' + m
      var d = day
      if (d < 10) d = '0' + d
      return y + '-' + m + '-' + d
    }
  }
}
</script>

<style lang="scss" scoped>
.calendar_box {
  .popup{
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0,0,0,0.5);
    z-index: 999;
    .calendar{
      width: 100%;
      position: absolute;
      bottom: 0;
      border-top-left-radius: 0.5rem;
      border-top-right-radius: 0.5rem;
      background-color: #fff;
      .calendar_title{
        font-size: 0.5rem;
        color: #323233;
        text-align: center;
        margin: 0.2rem 0;
        position: relative;
        i{
          position: absolute;
          right: 10px;
          font-size: 0.8rem;
          color: #c8c9cc;
        }
      }
      .week{
        font-size: 0.4rem;
        display: flex;
        justify-content: space-around;
        margin: 0.5rem 0;
      }
      .date_num{
        display: flex;
        flex-wrap: wrap;
        .nums{
          width: 14.285%;
          height: 45px;
          font-size: 16px;
          cursor: pointer;
          text-align: center;
          display: flex;
          align-items: center;
          justify-content: center;
          text-align: center;
          .other-month{
            padding: 5px;
            color: gainsboro;
          }
          .active{
            padding: 10px;
            border-radius: 50%;
            background: #00b8ec;
            color: #fff;
          }
        }
      }
      .year_month_box{
        margin-top: 0.6rem;
        display: flex;
        justify-content: space-around;
        font-size: 0.45rem;
        i{
          font-size: 0.5rem;
        }
      }
    }
  }
}
</style>
