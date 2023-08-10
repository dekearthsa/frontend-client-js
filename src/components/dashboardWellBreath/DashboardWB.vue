<script setup>
import {ref} from "vue";

import AirBadVue from '../icons/AirBad.vue';
import AirGoodVue from '../icons/AirGood.vue';
import AirNormalVue from '../icons/AirNormal.vue';
import FanIconVue from '../icons/FanIcon.vue';
import SunIconVue from "../icons/SunIcon.vue";
import WellBreathIcon from '../icons/WellBreathIcon.vue';
import MoonIconVue from "../icons/MoonIcon.vue";
import VocIconVue from "../icons/VocIcon.vue";
import TempIconVue from "../icons/TempIcon.vue";
import Pm25IconVue from "../icons/Pm25Icon.vue";
import FilterIconVue from "../icons/FilterIcon.vue";
import Co2IconVue from "../icons/Co2Icon.vue";
import HumidIconVue from "../icons/HumidIcon.vue";
import BotIconVue from "../icons/BotIcon.vue";
import ManaulIconVue from "../icons/ManaulIcon.vue";

const cssSystemActive = ref("");
const cssSystemActiveBTN = ref("");
const textSystemActive = ref("");

const cssIAQStatus = ref("iaq-good");

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
    <div class="h-[80vh]">
        <div class="flex justify-between title m-3">
            <div class="flex">
                <div><WellBreathIcon/></div>
                <div class="font-bold text-gray-500 mt-3 ml-5">WELL BREATH</div>
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
                    <div class="set-btn">
                        <div class="status-alert bg-red-500 rounded-full w-8 h-8"></div>
                        <!-- <div class="bg-gray-500 rounded-full w-8 h-8"></div>
                        <div class="bg-green-500 rounded-full w-8 h-8"></div> -->
                    </div>
                    <div class="set-param mr-5 text-[14px] font-bold">
                        <div class="flex">
                            <div class="mr-2"><FanIconVue/></div>
                            <div>Supply fan low</div>
                        </div>
                        <div class="flex">
                            <div class="mr-2"><FanIconVue/></div>
                            <div>Exhaust fan</div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="set-control  h-[90px] rounded-lg  mb-5" :class="cssIAQStatus">
                <div class="label-title font-bold text-gray-500 text-[12px] mb-2 ">
                    AIR QUAlITY
                </div>
                <div class="flex justify-between btn-action"> 
                    <div class="set-btn">
                        <AirGoodVue/>
                        <!-- <AirNormalVue/>
                        <AirBadVue/> -->
                    </div>
                    <div class="set-param mr-5 text-[14px] font-bold">
                        <div class="">
                            <div class="text-cyan-500">AIR QUAlITY GOOD</div>
                            <!-- <div class="text-green-500">Air quality fine</div>
                            <div class="text-red-700">Air quality bad</div> -->
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
            <div class="set-pm2 mt-2 items-center">
                <div class="val-pm2 text-center text-[20px] font-bold  mb-1">30</div>
                <div class="flex icon-pm2">
                    <div><Pm25IconVue/></div>
                    <div class="font-bold text-[10px] mt-2 ml-1 text-gray-500">PM2.5</div>
                </div>
            </div>
            <div class="border-r-[1px] border-gray-300"></div>
            <div class="set-temp-co2">
                <div class="flex set-temp mb-3">
                    <div class="icon-temp">
                        <TempIconVue/>
                    </div>
                    <div lass="val-temp font-bold">
                        27.4&#8451;
                    </div>
                </div>  
                <div class="flex set-co2">
                    <div class="icon-co2">
                        <Co2IconVue/>
                    </div>
                    <div class="val-co2 mt-1 ml-1">
                        200
                    </div>
                </div>
            </div>
            <div class="border-r-[1px] border-gray-300"></div>
            <div class="set-humid-voc">
                <div class="flex set-humid">
                    <div class="icon-humid">
                        <HumidIconVue/>
                    </div>
                    <div class="val-humid">
                        50
                    </div>
                </div>
                <div class="flex set-voc mt-2">
                    <div class="icon-voc">
                        <div>
                            <VocIconVue/>
                        </div>
                        <div class="text-[10px] text-center">
                            VOC
                        </div>
                    </div>
                    <div class="val-voc mt-2 ml-1">
                        11
                    </div>
                </div>
            </div>
            <div class="border-r-[1px] border-gray-300"></div>
            <div class="set-filter text-center mt-2">
                <div class="val-filter mb-2 font-bold">
                    10%
                </div>
                <div class="icon-filter font-bold text-[11px] text-gray-500">
                    <div></div>
                    <div class="flex">
                        <FilterIconVue/>
                        <div class="mr-1 mt-1">Filter</div>
                    </div>
                </div>
            </div>  
        </div>
    </div>
</template>

<style scoped>
hr.style-two {
    border: 0;
    height: 1px;
    background-image: linear-gradient(to right, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.75), rgba(0, 0, 0, 0));
}

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

</style>