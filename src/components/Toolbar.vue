

<template>
    <div id="toolbar" class="bg-gray-700">
        <div class="flex w-full">
            <div class="flex gap-3 my-3 justify-between items-center w-full px-5">
                <div class="flex gap-3"><button class="primary-btn text-white">Record</button>
                    <div class="flex gap-3 items-center">
                        <div class="cursor-pointer">
                            <ChevronLeft v-show="x !== 0" @click="() => scrollHorizentally(-100)" />
                        </div>
                        <div class="flex gap-2 overflow-x-hidden max-w-[600px] items-center" @mousewheel="scrollX"
                            ref="container">
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />
                            <CustomSelect :multi="false" title="Random title" :value="null" :options="data" />

                        </div>
                        <div class="cursor-pointer">
                            <ChevronRight class="cursor-pointer" v-show="x < 500" @click="() => scrollHorizentally(100)" />
                        </div>
                        <div><button class="bg-red-600 py-1 px-2 rounded-md text-white">Reset</button></div>
                    </div>

                </div>

            </div>
        </div><!----><!---->
    </div>
</template>

<script setup>
import ChevronLeft from './ChevronLeft.vue';
import ChevronRight from './ChevronRight.vue';
import CustomSelect from './CustomSelect.vue';
import { ref } from 'vue'
const data = ref([
    {
        "name": "title 0",
        "description": "description 0"
    },
    {
        "name": "title 1",
        "description": "description 1"
    },
    {
        "name": "title 2",
        "description": "description 2"
    },
    {
        "name": "title 3",
        "description": "description 3"
    },
    {
        "name": "title 4",
        "description": "description 4"
    },
    {
        "name": "title 5",
        "description": "description 5"
    },
    {
        "name": "title 6",
        "description": "description 6"
    },
    {
        "name": "title 7",
        "description": "description 7"
    },
    {
        "name": "title 8",
        "description": "description 8"
    },
    {
        "name": "title 9",
        "description": "description 9"
    },
    {
        "name": "title 10",
        "description": "description 10"
    },
    {
        "name": "title 11",
        "description": "description 11"
    },
    {
        "name": "title 12",
        "description": "description 12"
    },
    {
        "name": "title 13",
        "description": "description 13"
    },
    {
        "name": "title 14",
        "description": "description 14"
    },
    {
        "name": "title 15",
        "description": "description 15"
    },
    {
        "name": "title 16",
        "description": "description 16"
    }
])
const container = ref(null)
const x = ref(0)

const scrollX = (e) => {
    const classNames = e.target.className
    if (classNames.includes('dropdown-element')) return
    container.value.scrollLeft += e.deltaY;
    x.value = container.value.scrollLeft

}
const scrollHorizentally = (number) => {
    if (number < 0)
        container.value.scrollLeft -= Math.abs(number)
    else
        container.value.scrollLeft += Math.abs(number)

    x.value = container.value.scrollLeft

}
</script>