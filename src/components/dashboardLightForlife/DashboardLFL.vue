<script setup>
import {ref} from "vue";

import LightForLifeIcon from '../icons/LightForLifeIcon.vue';
import BatteryMaxIcon from "../icons/BatteryMaxIcon.vue";
import BatteryMidIcon from "../icons/BatteryMidIcon.vue";
import BatteryLowIcon from "../icons/BatteryLowIcon.vue";
import WifiIconVue from "../icons/WifiIcon.vue";

const cssSystemActive = ref("");
const cssSystemActiveBTN = ref("");
const textSystemActive = ref("");
const LFLNumber1 = ref({deviceName:"light bedroom 1",batteryLevel: 100, isActive: true});
const LFLNumber2 = ref({deviceName:"light bedroom 2",batteryLevel:40, isActive: false});
const LFLNumber3 = ref({deviceName:"light bedroom 3",batteryLevel: 20, isActive: false});
const LFLNumber4 = ref({deviceName:"IR bathroom",batteryLevel:88, isActive: true});

const onLoadingAPI = () => {
    cssSystemActive.value = "system-active-off";
    textSystemActive.value = "SYSTEM OFF";
    cssSystemActiveBTN.value = "text-zinc-600";
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

</script>

<template>
    <div class="h-[65vh]">
        <div class="flex justify-between title m-3">
            <div class="flex">
                <div><LightForLifeIcon/></div>
                <div class="font-bold text-gray-500 mt-3 ml-5">LIGHT FOR LIFE</div>
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

            <div class="set-control h-[260px] rounded-lg mb-5 mt-6">
                <div  class="label-title font-bold text-gray-500 text-[12px] mb-5 ">
                    LIGHT ON
                </div>
                <div class=""> 
                    <table class="text-left w-[100%] font-bold text-gray-500 border-separate border-spacing-4">
                        <!-- <tr>
                            <th>Device</th>
                            <th>Contact</th>
                            <th>Country</th>
                        </tr> -->
                        <tr>
                            <td class="">
                                <svg v-if="LFLNumber1.isActive === false" xmlns="http://www.w3.org/2000/svg" fill="#717171" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                                </svg>
                                <svg v-if="LFLNumber1.isActive === true" xmlns="http://www.w3.org/2000/svg" fill="#F0FF00" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                                </svg>
                            </td>
                            <td>{{LFLNumber1.deviceName}}</td>
                            <td >
                                <BatteryMaxIcon v-if="LFLNumber1.batteryLevel <= 100 && LFLNumber1.batteryLevel > 67" />
                                <BatteryMidIcon v-if="LFLNumber1.batteryLevel <= 67 && LFLNumber1.batteryLevel > 34"/>
                                <BatteryLowIcon  v-if="LFLNumber1.batteryLevel <= 34"/>
                            </td>
                        </tr>
                        <tr>
                            <td>
                                <svg v-if="LFLNumber2.isActive === false" xmlns="http://www.w3.org/2000/svg" fill="#717171" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                                </svg>
                                <svg v-if="LFLNumber2.isActive === true" xmlns="http://www.w3.org/2000/svg" fill="#F0FF00" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                                </svg>
                            </td>
                            <td>{{LFLNumber2.deviceName}}</td>
                            <td >
                                <BatteryMaxIcon v-if="LFLNumber2.batteryLevel <= 100 && LFLNumber2.batteryLevel > 67" />
                                <BatteryMidIcon v-if="LFLNumber2.batteryLevel <= 67 && LFLNumber2.batteryLevel > 34"/>
                                <BatteryLowIcon  v-if="LFLNumber2.batteryLevel <= 34"/>
                            </td>
                        </tr>
                        <tr>
                            <td>
                                <svg v-if="LFLNumber3.isActive === false" xmlns="http://www.w3.org/2000/svg" fill="#717171" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                                </svg>
                                <svg v-if="LFLNumber3.isActive === true" xmlns="http://www.w3.org/2000/svg" fill="#F0FF00" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                                </svg>
                            </td>
                            <td>{{LFLNumber3.deviceName}}</td>
                            <td >
                                <BatteryMaxIcon v-if="LFLNumber3.batteryLevel <= 100 && LFLNumber3.batteryLevel > 67" />
                                <BatteryMidIcon v-if="LFLNumber3.batteryLevel <= 67 && LFLNumber3.batteryLevel > 34"/>
                                <BatteryLowIcon  v-if="LFLNumber3.batteryLevel <= 34"/>
                            </td>
                        </tr>
                        <tr>
                            <td class="flex">
                                <WifiIconVue/>
                                <svg v-if="LFLNumber4.isActive === false" xmlns="http://www.w3.org/2000/svg" fill="#717171" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                                </svg>
                                <svg v-if="LFLNumber4.isActive === true" xmlns="http://www.w3.org/2000/svg" fill="#F0FF00" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                                </svg>
                            </td>
                            <td>{{LFLNumber4.deviceName}}</td>
                            <td >
                                <BatteryMaxIcon v-if="LFLNumber4.batteryLevel <= 100 && LFLNumber4.batteryLevel > 67" />
                                <BatteryMidIcon v-if="LFLNumber4.batteryLevel <= 67 && LFLNumber4.batteryLevel > 34"/>
                                <BatteryLowIcon  v-if="LFLNumber4.batteryLevel <= 34"/>
                            </td>
                        </tr>
                    </table>
                    <!-- <div>
                        <div>
                            <svg v-if="LFLNumber1.isActive === false" xmlns="http://www.w3.org/2000/svg" fill="#717171" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                            </svg>
                            <svg  v-if="LFLNumber1.isActive === true" xmlns="http://www.w3.org/2000/svg" fill="#F0FF00" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                            </svg>
                        </div>
                        <div class="text-center text-[12px]">
                            <div>{{LFLNumber1.deviceName}}</div>
                            <div>{{LFLNumber1.subSystem}}</div>
                        </div>
                    </div> -->
                    <!-- <div>
                        <div>
                            <svg v-if="LFLNumber2.isActive === false" xmlns="http://www.w3.org/2000/svg" fill="#717171" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                            </svg>
                            <svg v-if="LFLNumber2.isActive === true" xmlns="http://www.w3.org/2000/svg" fill="#F0FF00" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                            </svg>
                        </div>
                    </div> -->
                    <!-- <div>
                        <div>
                            <svg v-if="LFLNumber3.isActive === false" xmlns="http://www.w3.org/2000/svg" fill="#717171" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                            </svg>
                            <svg v-if="LFLNumber3.isActive === true" xmlns="http://www.w3.org/2000/svg" fill="#F0FF00" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                            </svg>
                        </div>
                    </div> -->
                    <!-- <div>
                        <div>
                            <svg v-if="LFLNumber4.isActive === false" xmlns="http://www.w3.org/2000/svg" fill="#717171" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                            </svg>
                            <svg v-if="LFLNumber4.isActive === true" xmlns="http://www.w3.org/2000/svg" fill="#F0FF00" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
                            </svg>
                        </div>
                    </div> -->
                </div>
            </div>

        </div>
    </div>
</template>

<style scoped>

</style>