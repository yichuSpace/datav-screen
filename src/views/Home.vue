<template>
  <div class="home">
    <Loading :width="200" :height="200" v-if="loading">
      <div class="loading-text">加载中...</div>
    </Loading>

    <Container :options="{ width: 1920, height: 1080 }" v-else>
      <div class="container">
        <div class="header-box">
          <top-header></top-header>
        </div>
        <div class="line"></div>
        <div class="container-box">
          <div class="container-box-left">
            <div class="left-box-1">
              <total-user :today-user="todayUser" :growth-last-day="growthLastDay" :growth-last-month="growthLastMonth" />
            </div>
            <div class="left-box-2">
              <average-age :data="ageData" :avg-age="averageAge" />
            </div>
            <div class="left-box-3"></div>
            <div class="left-box-4"></div>
            <div class="left-box-5"></div>
            <div class="left-box-6"></div>
          </div>
          <div class="container-box-right">
            <div class="right-box-1"></div>
            <div class="right-box-2"></div>
            <div class="right-box-bottom">
              <div class="right-bottom-left">
                <div class="right-bottom-left-1"> </div>
                <div class="right-bottom-left-2"> </div>
                <div class="right-bottom-left-3"> </div>
                <div class="right-bottom-left-4"> </div>
              </div>
              <div class="right-bottom-right">
                <div class="right-bottom-right-1"> </div>
                <div class="right-bottom-right-2"> </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </Container>
  </div>
</template>

<script>
import TopHeader from '@/components/TopHeader/'
import TotalUser from '@/components/TotalUser/'
import AverageAge from '@/components/AverageAge/'
import useScreenData from '@/hooks/useScreenData'
import { ref } from 'vue'
export default {
  name: 'Home',

  components: {
    TopHeader, TotalUser, AverageAge
  },
  setup (ctx) {
    const loading = ref(true)
    setTimeout(() => {
      loading.value = false
    }, 1000)
    const screenData = useScreenData()
    return {
      loading,
      ...screenData,
      options: {
        xAxis: {
          data: ['a', 'b', 'c', 'd']
        },
        yAxis: {},
        series: [{
          name: 'sales',
          type: 'bar',
          data: [10, 15, 20, 25]
        }]
      }
    }
  }
}
</script>
<style lang="scss" scoped>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  color: #fff;
  font-size: 48px;
  background: #666;
  .loading-text {
    font-size: 20px;
    margin-top: 10px;
  }
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    .header-box {
      width: 100%;
      height: 100px;
      background: pink;
    }
    .line {
      width: 100%;
      height: 5px;
      background: rgb(92, 88, 89);
    }

    &-box {
      display: flex;
      flex: 1;
      width: 100%;
      &-left {
        flex: 0 0 344px;
        background: red;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        height: 100%;
        padding-bottom: 20px;
        box-sizing: border-box;
        .left-box-1 {
          height: 200px;
          background: grey;
        }

        .left-box-2 {
          height: 220px;
          background: grey;
        }

        .left-box-3 {
          height: 180px;
          background: grey;
        }

        .left-box-4 {
          height: 130px;
          background: grey;
        }

        .left-box-5 {
          height: 320px;
          background: grey;
        }

        .left-box-6 {
          height: 160px;
          background: grey;
        }
      }
      &-right {
        flex: 1;
        background: 333;
        display: flex;
        flex-direction: column;
        margin-left: 10px;
        background: pink;
        .right-box-1 {
          height: 100px;
          background: grey;
        }
        .right-box-2 {
          width: 100%;
          height: 48px;
          background: grey;
          margin: 5px 0;
        }
        .right-box-bottom {
          flex: 1;
          display: flex;
          padding-bottom: 20px;
          .right-bottom-left {
            flex: 0 0 1000px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            width: 1000px;
            background: #000;
            &-1 {
              height: 400px;
              background: grey;
            }
            &-2 {
              height: 80px;
              background: grey;
            }
            &-3 {
              height: 150px;
              background: grey;
            }
            &-4 {
              height: 150px;
              background: grey;
            }
          }
          .right-bottom-right {
            flex: 1;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            margin-left: 10px;
            &-1 {
              height: 400px;
              background: grey;
            }
            &-2 {
              height: 80px;
              background: grey;
            }
          }
        }
      }
    }
  }
}
</style>
