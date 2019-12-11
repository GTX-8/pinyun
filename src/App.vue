<template>
  <div id="app">
    <van-nav-bar title="政策兑现">
      <van-icon name="cross" slot="left" />
      <van-icon name="search" slot="right" />
    </van-nav-bar>
    <van-pull-refresh v-model="isLoading" @refresh="onRefresh">
      <van-list
        v-model="listLoading"
        :finished="finished"
        finished-text="没有更多了"
        @load="onLoad"
      >
        <div class="policyTitle">
          <div class="policyTitle-items" v-for="(item,index) in options" :key="index">
            <p>{{item.title}}</p>
            <input type="text" :value="item.value">
          </div>
          <div class="policyTitle-content">
            <div class="policyTitle-content-left">全部</div>
            <div class="policyTitle-content-right">
              <div class="policyTitle-content-right-item">在办</div>
              <div class="policyTitle-content-right-item">已完结</div>
              <div class="policyTitle-content-right-item">不予兑换</div>
              <div class="policyTitle-content-right-item">中止申请</div>
            </div>
          </div>
          <div class="policyTitle-footer">查询</div>
        </div>
        <div class="policyContent">
          <div class="policyContent-item" v-for="(item,index) in 9" :key="index"> 
            <div class="policyContent-item-left">0{{index+1}}</div>
            <div class="policyContent-item-center">
              <div class="policyContent-item-center-top">投资促进局一事一议或一企一策的扶持奖金</div>
              <div class="policyContent-item-center-bottom">TC20180904-010 | 2018-08-04 15:55:09</div>
            </div>
            <div class="policyContent-item-right">
              <P>1:00元</P>
              <p>预审不通过</p>
            </div>
          </div>
        </div>
      </van-list>
    </van-pull-refresh>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      count: 0,
      isLoading: false,
      listLoading: false, // 是否显示没有更多数据  为true 时不可上拉  
      finished:false,
      options: [
        { title: '申请事项编号', value: 'TC20180904-010' },
        { title: '申请开始时间', value: '2018-08-04' },
        { title: '事项名称', value: '2017年度企业管理' },
        { title: '结束时间', value: '2018-09-04' }
      ]
    }
  },

  methods: {
    onRefresh() {
      setTimeout(() => {
        this.$toast('刷新成功');
        this.isLoading = false;
        this.count++;
      }, 500);
    },
    onLoad() {
      setTimeout( ()=> {
        this.finished = true
      })
    }
  }
}
</script>

<style lang="less">
 #app {
   .van-nav-bar .van-icon {
     font-size: 20px;
     color: #171717;
   }
 }
</style>
<style lang="less" scoped>
  #app {
    max-height: 100%;
    .policyTitle {
      padding: 10px 15px;
      border: 1px solid #eaeaea;
      margin: 10px 10px 20px 10px;
      border-radius: 5px;
      &-items {
        display: flex;
        align-items: center;
        margin-bottom: 5px;
        p {
          color: #a2a2a2;
          margin: 0 10px 0 0;
          flex: 0 0 100px;
          text-align: right;
        }
        input {
          background: #fafafa;
          border: 1px solid #eaeaea;
          height: 40px;
          flex: 1;
          padding-left: 10px;
          &:focus {
            outline: none
          }
        }
      }
      &-content {
        display: flex;
        height: 100px;
        margin: 10px 0;
        &-left {
          width: 33%;
          border: 1px solid #eaeaea;
          display: flex;
          justify-content: center;
          align-items: center;
          margin-right: 10px;
          border-radius: 5px;
        }
        &-right {
          display: flex;
          flex-wrap: wrap;
          &-item {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 46.5%;
            height: 41%;
            border: 1px solid #eaeaea;
            border-radius: 3px;
            &:nth-child(1) {
              margin: 0 10px 10px 0;
            }
            &:nth-child(3){
              margin-right: 10px;
            }
          }
        }
      }
      &-footer {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 45px;
        background-color: #00a0ea;
        color: #fff;
      }
    }
    .policyContent {
      &-item {
        display: flex;
        padding: 8px 0 8px 10px; 
        border: 1px solid #eaeaea;
        margin: 0 10px 10px 10px;
        border-radius: 5px;
        &-left {
          width: 30px;
          height:30px;
          border-radius: 15px;
          background-color: #eeeeee;
          color: #a8a8a8;
          display: flex;
          justify-content: center;
          align-items: center;
          margin-right: 6px;
        }
        &-center {
          flex: 1;
          &-bottom {
            font-size: 12px;
            color: #cecece;
            margin-top: 10px;
          }
        }
        &-right {
          width: 100px;
          margin-left: 6px;
          background-color: #00a0ea;
          border-radius: 8px 0 0 8px;
          color:#fff;
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
          p {
            margin:0;
          }
        }
      }
    }
  }
</style>
