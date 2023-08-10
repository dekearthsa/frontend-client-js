<script setup>
import Navbar from '../components/Navbar.vue';
import DashboardAD from '../components/dashboardAlwayDry/DashboardAD.vue';
import DashboardLFL from '../components/dashboardLightForlife/DashboardLFL.vue';
import DashboardWB from '../components/dashboardWellBreath/DashboardWB.vue';

</script>

<template>
  <div class="set-home">
      <div>
        <Navbar/>
      </div>
      <div class="grid grid-cols-3">
        <DashboardWB class="box-sh rounded-md m-5"/>
        <DashboardAD class="box-sh rounded-md m-5"/>
        <DashboardLFL class="box-sh rounded-md m-5"/>
      </div>
      <div class="box">
        <!-- stuff -->
        <p class="bet_time mr-[80px] text-[35px] translate-y-[-40px] font-bold text-cyan-800">Journey Solution</p>
      </div>
  </div>
  
</template>



<style scoped>
.box-sh{
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
}

.box {
  position:relative;
}
.bet_time {
  position:absolute;
  bottom:0;
  right:0;
}

</style>