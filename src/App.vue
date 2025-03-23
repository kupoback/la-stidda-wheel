<script setup>
/**
 * Vue Scripts
 * @link https://github.com/zohaibtariq/vuewinwheel#readme
 */
import {ref, onMounted} from 'vue';
import {VueWinWheel} from '@zohaibtariq/vuewinwheel'
import '@zohaibtariq/vuewinwheel/dist/style.css';

const winWheel = ref();
const contestants = ref([]);

// set custom canvas width
const canvasWidth = 500;
 // set custom canvas height
const canvasHeight = 500;
// Segment atr which you want to stop at
const stopAt = 3;

const spinWinWheel = () => {
    // if you miss this sound will not play after first run
    spinStartTime = Date.now()

    // winWheelInstances is only required for the (2 part wheel)
    if (winWheel.value) winWheel.value.spin()
};

const spinWinWheelStopAt = () => {
     // if you miss this sound will not play after first run
    spinStartTime = Date.now()

    if (winWheel.value) winWheel.value.spinAndStopAt(stopAt)
};


const allOptions = {
    ...options,
    outerRadius: (canvasWidth / 2) - (options.lineWidth || 1)
};

onMounted(() => {
    allOptions.outerRadius = (canvasWidth / 2) - (options.lineWidth || 1);
});

</script>

<template>
    <div class="text-gray-900 bg-gray-100 font-serif dark:bg-gray-800 dark:text-white h-max">
        <main>
            <h1>La Stidda Wheel</h1>
            <VueWinWheel
                ref="winWheel"
                :options="allOptions"
                :canvasWidth="canvasWidth"
                :canvasHeight="canvasHeight"
                :stopAt="stopAt"
            />

        </main>
    </div>
</template>

<script>
    export default {
        name: 'Wheel of Fotune',
    };
</script>

<style lang="scss" scoped></style>
