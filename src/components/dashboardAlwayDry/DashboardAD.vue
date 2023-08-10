<script setup>
import {ref} from "vue";

import AlwaydryIcon from '../icons/AlwaydryIcon.vue';
import FanIconVue from '../icons/FanIcon.vue';
// import HumidIconVue from "../icons/HumidIcon.vue";
import MonitorIconVue from "../icons/MonitorIcon.vue";
import HumidIconADVue from "../icons/HumidIconAD.vue";

import BotIconVue from "../icons/BotIcon.vue";
import ManaulIconVue from "../icons/ManaulIcon.vue";

const cssSystemActive = ref("");
const cssSystemActiveBTN = ref("");
const textSystemActive = ref("");


const cssHaddleMode = ref("");
const cssHaddleModeBTN = ref("");
const textHaddleMode = ref("");

const onLoadingAPI = () => {
    cssSystemActive.value = "system-active-off";
    textSystemActive.value = "SYSTEM OFF";
    cssSystemActiveBTN.value = "text-zinc-600";
    cssHaddleMode.value = "auto-mode-off";
    cssHaddleModeBTN.value = "text-yellow-600";
    textHaddleMode.value = "AUTO MODE OFF";
}

onLoadingAPI();

const haddleAutoModel = () => {
    if(cssSystemActive.value === "system-active-on"){
        cssSystemActive.value = "system-active-off";
        textSystemActive.value = "SYSTEM OFF";
        cssSystemActiveBTN.value = "text-zinc-600";
    }else{
        cssSystemActive.value = "system-active-on";
        textSystemActive.value = "SYSTEM ON";
        cssSystemActiveBTN.value = "text-cyan-500";
    }
}

const haddleAutoMode = () => {
    if(cssHaddleMode.value === "auto-mode-on"){
        cssHaddleMode.value = "auto-mode-off";
        cssHaddleModeBTN.value = "text-yellow-600";
        textHaddleMode.value = "AUTO MODE OFF";
    }else{
        cssHaddleMode.value = "auto-mode-on";
        cssHaddleModeBTN.value = "text-indigo-600";
        textHaddleMode.value = "AUTO MODE ON";
    }
}


</script>

<template>
    <div class="">
        <div class="flex justify-between title m-3 ">
            <div class="flex">
                <div><AlwaydryIcon/></div>
                <div class="font-bold text-gray-500 mt-3 ml-5">ALWAY DRY</div>
            </div>
            <div class="font-bold text-gray-500 mt-3">
                <label for="system"></label>
                <select name="system" id="system">
                    <option value="zone1">zone1</option>
                    <option value="zone2">zone2</option>
                </select>
            </div>
        </div>
        <div class=" w-[300px] m-auto">

            <div class="set-control h-[90px] rounded-lg mb-5 mt-6"  :class="cssSystemActive">
                <div class="label-title font-bold text-gray-500 text-[12px] mb-2 ">
                    SYSTEM
                </div>
                <div class="flex justify-between btn-action"> 
                    <div class="set-btn">
                        <label class="relative inline-flex items-center cursor-pointer">
                            <input type="checkbox"  class="sr-only peer"  @click="haddleAutoModel(cssSystemActive)"/>
                            <div class="w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-300 dark:peer-focus:ring-blue-500 rounded-full peer dark:bg-gray-400 peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all dark:border-gray-600 peer-checked:bg-blue-500"></div>
                        </label>
                    </div>
                    <div class="set-param mr-5 font-bold">
                        <div :class="cssSystemActiveBTN">{{textSystemActive}}</div>
                    </div>
                </div>
            </div>

            <div class="set-control  h-[90px] rounded-lg  mb-5" >
                <div class="label-title font-bold text-gray-500 text-[12px] mb-2 ">
                    FAN ACTIVE STATUS 
                </div>
                <div class="flex justify-between btn-action"> 
                    <div class="flex animate-flicker">
                        <div class=" status-alert bg-red-500 rounded-full w-8 h-8"></div>
                        <div class="text-[10px] text-red-600 font-bold mt-2 ml-2">Working...</div>
                        <!-- <div class="bg-gray-500 rounded-full w-8 h-8"></div>
                        <div class="bg-green-500 rounded-full w-8 h-8"></div> -->
                    </div>
                    <div class="set-param mr-5 text-[14px] font-bold">
                        <div class="flex">
                            <div class="mr-2"><FanIconVue/></div>
                            <div>Exhaust fan</div>
                        </div>
                        <div class="flex">
                            <div class="mr-2"><FanIconVue/></div>
                            <div>Dry fan</div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="set-control  h-[90px] rounded-lg  mb-5" >
                <div class="label-title font-bold text-gray-500 text-[12px] mb-2 ">
                    TIME REMAINING  
                </div>
                <div class="flex justify-between btn-action"> 
                    <div class="set-btn ">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10 ml-3">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z" />
                        </svg>
                    </div>
                    <div class="set-param mr-5 text-[20px] font-bold ml-5">
                        <div class="">
                            <div class="text-gray-500">15 min remaining</div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="set-control  h-[90px] rounded-lg  mb-5" :class="cssHaddleMode">
                <div class="label-title font-bold text-gray-500 text-[12px] mb-2 ">
                    AUTO MODE
                </div>
                <div class="flex justify-between btn-action"> 
                    <div class="set-btn">
                        <label class="relative inline-flex items-center cursor-pointer">
                            <input type="checkbox" class="sr-only peer" @click="haddleAutoMode">
                            <div class="w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-300 dark:peer-focus:ring-blue-500 rounded-full peer dark:bg-gray-400 peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all dark:border-gray-600 peer-checked:bg-blue-500"></div>
                        </label>
                    </div>
                    <div class="translate-y-[-24px] set-param mr-5 text-[14px] font-bold ">
                        <div class="">
                            <BotIconVue v-if="textHaddleMode === 'AUTO MODE ON'" />
                            <ManaulIconVue v-if="textHaddleMode === 'AUTO MODE OFF'" />
                            <div :class="cssHaddleModeBTN">{{textHaddleMode}}</div>
                        </div>
                    </div>
                </div>
            </div>

        </div>
        <hr/>
        <div class="flex justify-around mt-5 ">
            <div class="flex set-pm2 mt-2 items-center">
                <div class="flex icon-pm2">
                    <div><HumidIconADVue/></div>
                </div>
                <div class="val-pm2 text-center text-[20px] font-bold  mb-1">30%</div>
            </div>
            <div class="border-r-[1px] border-gray-300"></div>
            <div class="flex justify-around set-filtermt-2">
                <div class="icon-filter font-bold text-[11px] text-gray-500">
                    <div class="text-center">  
                        <MonitorIconVue/>
                        <div class="mr-1 mt-1">MOTION</div>
                    </div>
                </div>
                <div class="val-filter mb-2 font-bold mt-4 ml-2 text-[20px]">
                    50%
                </div>
            </div>  
        </div>
    </div>
    
</template>

<style>


.set-control{
    padding: 10px;
    box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
}

.status-alert{
    box-shadow: rgba(0, 0, 0, 0.15) 2.4px 2.4px 3.2px;
}

.system-active-on{
    background: rgb(255,255,255);
    background: linear-gradient(140deg, rgba(255,255,255,1) 54%, rgba(151,250,255,1) 87%, rgba(59,189,196,1) 100%);
}

.system-active-off{
    background: rgb(255,255,255);
    background: linear-gradient(140deg, rgba(255,255,255,1) 54%, rgb(118, 118, 118) 87%, rgb(50, 50, 50) 100%);
}

.iaq-good{
    background: rgb(255,255,255);
    background: linear-gradient(140deg, rgba(255,255,255,1) 54%, rgba(151,250,255,1) 87%, rgba(59,189,196,1) 100%);
}

.iaq-fine{
    background: rgb(255,255,255);
    background: linear-gradient(140deg, rgba(255,255,255,1) 54%, rgba(151,255,152,1) 87%, rgba(59,196,104,1) 100%);
}

.iaq-bad{
    background: rgb(255,255,255);
    background: linear-gradient(140deg, rgba(255,255,255,1) 54%, rgba(255,151,151,1) 87%, rgba(196,59,59,1) 100%);
}

.auto-mode-on{
    background: rgb(255,255,255);
    background: linear-gradient(140deg, rgba(255,255,255,1) 54%, rgba(151,159,255,1) 87%, rgba(59,67,196,1) 100%);
}

.auto-mode-off{
    background: rgb(255,255,255);
    background: linear-gradient(140deg, rgba(255,255,255,1) 54%, rgba(255,244,151,1) 87%, rgba(196,196,59,1) 100%);
}

@keyframes animationFade {
    0%   { opacity:1; }
    50%  { opacity:0; }
    100% { opacity:1; }
  }
  @-o-keyframes animationFade{
    0%   { opacity:1; }
    50%  { opacity:0; }
    100% { opacity:1; }
  }
  @-moz-keyframes animationFade{
    0%   { opacity:1; }
    50%  { opacity:0; }
    100% { opacity:1; }
  }
  @-webkit-keyframes animationFade{
    0%   { opacity:1; }
    50%  { opacity:0; }
    100% { opacity:1; }
  }
  .animate-flicker {
     -webkit-animation: animationFade 2s infinite;
     -moz-animation: animationFade 2s infinite;
     -o-animation: animationFade 2s infinite;
      animation: animationFade 2s infinite;
  }

</style>