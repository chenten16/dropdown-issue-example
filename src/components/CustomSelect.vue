<template>
  <Listbox v-model="selectedOptions" :multiple="multi">
    <div>
      <ListboxButton
        class="relative min-h-[36px] flex-1 max-w-[150px] w-full cursor-default rounded-lg !bg-black/20 font-medium py-2 pl-3 pr-10 text-left shadow-md focus:outline-none focus-visible:border-indigo-500 focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-opacity-75 focus-visible:ring-offset-2 focus-visible:ring-offset-orange-300 sm:text-sm">
        <span class="block truncate text-white">{{ selectLabel }}</span>
        <span class="pointer-events-none absolute inset-y-0 right-0 flex items-center pr-2">
          <!-- <ChevronUpDownIcon class="h-5 w-5 text-gray-400" aria-hidden="true" /> -->
        </span>
      </ListboxButton>

      <transition leave-active-class="transition duration-100 ease-in" leave-from-class="opacity-100"
        leave-to-class="opacity-0">
        <ListboxOptions
          class="z-10 absolute max-w-[200px] mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none sm:text-sm">
          <ListboxOption v-slot="{ active, selected }" v-for="option in options" :key="option.name" :value="option"
            as="template">
            <li class="dropdown-element" :class="[
              active ? 'bg-teal-100 text-teal-900' : 'text-gray-900',
              'relative cursor-default select-none py-2 pl-10 pr-4',
            ]">
              <span class="dropdown-element" :class="[
                selected ? 'font-medium' : 'font-normal',
                'block truncate',
              ]">{{ option.name }}</span>
              <span v-if="selected" class="dropdown-element absolute inset-y-0 left-0 flex items-center text-teal-600">
                <!-- <CheckIcon class="h-5 w-5" aria-hidden="true" /> -->
              </span>
            </li>
          </ListboxOption>
        </ListboxOptions>
      </transition>
    </div>
  </Listbox>
</template>
  
<script setup>
import { computed, ref, watch } from "vue";
import {
  Listbox,
  ListboxButton,
  ListboxOptions,
  ListboxOption,
} from "@headlessui/vue";
// import { CheckIcon, ChevronUpDownIcon } from '@heroicons/vue/20/solid'
const props = defineProps({
  options: Array,
  title: String,
  maxWidth: Number,
  value: Array | null,
  multi: {
    type: Boolean,
    default: false,
  },
});
const selectedOptions = ref(props.value);

const selectLabel = computed(() => {
  if (!props.value || props.value.length == 0) return props.title;

  return props.multi
    ? props.value.map((el) => el.name).join(", ")
    : props.value.name;
});
const emit = defineEmits(["update"]);
watch(
  () => props.value,
  (val) => {
    selectedOptions.value = val;
  }
);
watch(selectedOptions, (val) => {
  emit("update", val);
});
</script>
  