<template>
  <div class="e-div-1">
    <div style="float: left; width: 100px; margin-left: 180px">
      <img class="logo" src="../../assets/LOGO/logo.png" style="width: 200px" />
    </div>
    <el-tabs class="customer-tab" type="card" @tab-click="jump" v-model="tabName">
      <el-tab-pane class="e-tab-item" v-for="(tab, index) in tabs" :name="tab.refName" :key="index" :label="tab.name">
      </el-tab-pane>
    </el-tabs>
  </div>

  <div class="scroll-content" @scroll="onScroll" :style="'height:' + contentStyleObj.height">
    <div :ref="tabs[0].refName" class="scroll-item">
      <div>
        <about></about>
      </div>
    </div>
    <div :ref="tabs[1].refName" class="scroll-item">
      <div>
        <market></market>
      </div>
    </div>
    <div :ref="tabs[2].refName" class="scroll-item">
      <div>
        <services></services>
      </div>
    </div>

    <div :ref="tabs[3].refName" class="scroll-item">
      <div>
        <partnership></partnership>
      </div>
    </div>

    <div :ref="tabs[4].refName" class="scroll-item">
      <div>
        <team></team>
      </div>
    </div>


    <img src="../../assets/FOOTER/1.png" style="width: 73px; position:fixed;right:150px;bottom:100px;z-index: 2;"
      v-on:click="top" />

    <div style="width: 100%;height:420px;background-color:#3D86C6;position: relative;">
      <img src="../../assets/FOOTER/LOGO（WHT）.png" style="position: absolute; width: 190px; top: 80px; left: 190px" />
      <div style="position: absolute;top: 375px; left: 190px">
        <span style="font-size: 14px;color: white;">© 2022 TIDE Groups All Rights Reserved.</span>
      </div>

      <div style="position: absolute;top: 80px; left: 1200px">
        <span style="font-size: 24px;color: white;">CONNECT</span>
      </div>

      <div style="position: absolute;top: 110px; left: 1200px">
        <span style="font-size: 24px;color: white;">WITH</span>
      </div>

      <div style="position: absolute;top: 140px; left: 1200px">
        <span style="font-size: 24px;color: white;">US</span>
      </div>

      <div style="position: absolute;top: 80px; left: 1470px">
        <img src="../../assets/FOOTER/Twitter.png" style="width: 20px;" />
      </div>
      <div style="position: absolute;top: 80px; left: 1500px">
        <span style="font-size: 20px;color: white">Twitter</span>
      </div>

      <div style="position: absolute;top: 110px; left: 1470px">
        <img src="../../assets/FOOTER/Telegram.png" style="width: 20px;" />
      </div>
      <div style="position: absolute;top: 110px; left: 1500px">
        <span style="font-size: 20px;color: white">Telegram</span>
      </div>

      <div style="position: absolute;top: 140px; left: 1470px">
        <img src="../../assets/FOOTER/Email.png" style="width: 20px;" />
      </div>
      <div style="position: absolute;top: 140px; left: 1500px">
        <span style="font-size: 20px;color: white">Email</span>
      </div>

      <div style="position: absolute;top: 80px; left: 1770px">
        <span style="font-size: 20px;color: white">About</span>
      </div>
      <div style="position: absolute;top: 110px; left: 1770px">
        <span style="font-size: 20px;color: white">Market Making</span>
      </div>
      <div style="position: absolute;top: 140px; left: 1770px">
        <span style="font-size: 20px;color: white">Services</span>
      </div>
      <div style="position: absolute;top: 170px; left: 1770px">
        <span style="font-size: 20px;color: white">Partnerships</span>
      </div>
      <div style="position: absolute;top: 200px; left: 1770px">
        <span style="font-size: 20px;color: white">Our Team</span>
      </div>

      <div style="position: absolute;top: 85px; left: 590px">
        <input style="background-color: transparent;border-color: white;border-radius: 5px;width: 300px;height: 30px;"
          placeholder="NAME" />
      </div>
      <div style="position: absolute;top: 140px; left: 590px">
        <input style="background-color: transparent;border-color: white;border-radius: 5px;width: 300px;height: 30px;"
          placeholder="EMAIL" />
      </div>

      <div style="position: absolute;top: 195px; left: 590px">
        <textarea
          style="background-color: transparent;border-color: white;border-radius: 5px;width: 300px;height: 120px;"
          placeholder="LEAVE US A MESSAGE" />
      </div>

      <div style="position: absolute;top: 290px; left: 920px">
        <img src="../../assets/FOOTER/Submit（点击前）.png" style="width: 30px;" />
      </div>

    </div>
  </div>
</template>
   
<script>
import about from "../about/about.vue";
import market from "../market/market.vue";
import partnership from "../partnership/partnership.vue";
import services from "../services/services.vue";
import team from "../team/team.vue";
import wave from '../wave/wave.vue';

export default {
  name: "index",
  props: {},
  components: {
    about,
    market,
    partnership,
    services,
    team,
    wave
  },
  data() {
    return {
      tabIndex: "0",
      contentStyleObj: {
        height: "200px",
      },
      tabName: "ABOUT",
      tabs: [
        {
          name: "ABOUT",
          refName: "ABOUT",
        },
        {
          name: "MARTEK MAKING",
          refName: "MARTEK",
        },
        {
          name: "SERVICES",
          refName: "SERVICES",
        },
        {
          name: "PARTNERSHIPS",
          refName: "PARTNERSHIPS",
        },
        {
          name: "OUR TEAM",
          refName: "TEAM",
        },
      ],
    };
  },
  computed: {},
  watch: {},
  created() {
    this.getHight();
    window.addEventListener("resize", this.getHight);
  },
  destroyed() {
    window.removeEventListener("resize", this.getHight);
  },
  methods: {
    // tab click
    jump(tab, event) {
      let target = document.querySelector(".scroll-content");
      let scrollItems = document.querySelectorAll(".scroll-item");
      // 判断滚动条是否滚动到底部
      if (target.scrollHeight <= target.scrollTop + target.clientHeight) {
        this.tabIndex = tab.index.toString();
      }
      let totalY = scrollItems[tab.index].offsetTop - scrollItems[0].offsetTop; // 锚点元素距离其offsetParent(这里是body)顶部的距离(待滚动的距离)
      let distance = document.querySelector(".scroll-content").scrollTop; // 滚动条距离滚动区域顶部的距离
      // let distance = document.body.scrollTop || document.documentElement.scrollTop || window.pageYOffset // 滚动条距离滚动区域顶部的距离(滚动区域为窗口)
      // 滚动动画实现, 使用setTimeout的递归实现平滑滚动，将距离细分为50小段，10ms滚动一次
      // 计算每一小段的距离
      let step = totalY / 100;
      if (totalY > distance) {
        smoothDown(document.querySelector(".scroll-content"));
      } else {
        let newTotal = distance - totalY;
        step = newTotal / 100;
        smoothUp(document.querySelector(".scroll-content"));
      }

      // 参数element为滚动区域
      function smoothDown(element) {
        if (distance < totalY) {
          distance += step;
          element.scrollTop = distance;
          setTimeout(smoothDown.bind(this, element), 12);
        } else {
          element.scrollTop = totalY;
        }
      }

      // 参数element为滚动区域
      function smoothUp(element) {
        if (distance > totalY) {
          distance -= step;
          element.scrollTop = distance;
          setTimeout(smoothUp.bind(this, element), 12);
        } else {
          element.scrollTop = totalY;
        }
      }
    },
    // 滚动条滚动
    onScroll(e) {
      let scrollItems = document.querySelectorAll(".scroll-item");
      for (let i = scrollItems.length - 1; i >= 0; i--) {
        // 判断滚动条滚动距离是否大于当前滚动项可滚动距离
        let judge =
          e.target.scrollTop >=
          scrollItems[i].offsetTop - scrollItems[0].offsetTop - 500;
        if (judge) {
          this.tabIndex = i.toString();
          // 找对应的tab-name值
          this.tabName = this.tabs[this.tabIndex].refName;
          break;
        }
      }
    },
    getHight() {
      this.contentStyleObj.height = window.innerHeight - 120 + "px";
    },
    top: function () {
      this.jump({ "index": 0 }, 0);
    }
  },
};
</script>
   
<style lang="scss" scoped>
::v-deep.customer-tab {
  // width: 60%;
  //   height: 50px;
  //   background-color: #f5f7fa;
  padding: 4px;
  margin-left: 45%;
}

.e-div-1 {
  margin-top: 26px;
}

::-webkit-input-placeholder {
  color: white;
}

.scroll-content {
  margin-top: 30px;
  overflow-x: hidden;
  overflow-y: auto;
  padding-bottom: 25px;
}

// .scroll-item{
//     width: 100%;
// }

::v-deep.el-tabs--card>.el-tabs__header {
  border-bottom: none;
  margin: 0;

  .el-tabs__nav {
    // width: 70%;
    display: flex;
    justify-content: space-around;
    border: none;

    .el-tabs__item {
      width: 200px;
      text-align: center;
      border: none;
      font-weight: bold;
      //   font-size: 20px;
    }

    .is-active {
      border-radius: 45px;
      background-color: #3D86C6;
      color: #fff;
    }
  }
}
</style>
   
   