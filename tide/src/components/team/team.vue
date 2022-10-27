<template>
  <div class="P-about">
    <div style="position: relative">
      <!-- <img
        src="../../assets/PARTNERSHIPS/线条插图-3.png"
        style="width: 100%; position: absolute"
      /> -->
      <div style="
          font-size: 20px;
          font-weight: bold;
          position: absolute;
          top: 40px;
          left: 995px;
        ">
        <span>OUR TEAM</span>
      </div>

      <div style="
          font-size: 20px;
          font-weight: bold;
          position: absolute;
          top: 58px;
          left: 1030px;
        ">
        <span>——</span>
      </div>
      <div style="position: absolute; top: 218px; width: 50%; left: 510px">
        <el-carousel :interval="4000" type="card" height="610px">
          <el-carousel-item v-for="item in 6" :key="item">
            <el-card shadow="always" style="height: 300px">{{ item }}</el-card>
          </el-carousel-item>
        </el-carousel>
      </div>

      <div style="position: absolute;top: 1200px; width:100%; ">
        <wave style="width:1920px;height: 100px;"></wave>
      </div>
    </div>
  </div>
</template>
  
<script>
import wave from '../wave/wave.vue';
export default {};
</script>
  
<style scoped>
.P-about {
  height: 1300px;
}

.el-carousel__item h3 {
  color: #475669;
  opacity: 0.75;
  line-height: 200px;
  margin: 0;
  text-align: center;
}

.el-carousel__item:nth-child(2n) {
  background-color: #99a9bf;
}

.el-carousel__item:nth-child(2n + 1) {
  background-color: #d3dce6;
}
</style>
  