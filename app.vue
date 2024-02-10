<template>
  <div class="flex flex-col gap-8 p-8">
    <label class="flex flex-row gap-4 items-center [&>.checkbox]:hover:bg-neutral-100">
      <CheckboxRoot
        :checked="options['1'] && options['2']"
        class="shadow-blackA7 hover:bg-green3 flex h-[25px] w-[25px] appearance-none items-center justify-center rounded-[4px] bg-white shadow-[0_2px_10px] outline-none"
        @update:checked="
            $event
                ? ((options['1'] = true),
                    (options['2'] = true))
                : ((options['1'] = false),
                    (options['2'] = false))
        "
      >
        <CheckboxIndicator class="bg-white h-full w-full rounded flex items-center justify-center">
          <Icon name="radix-icons:check" class="h-3.5 w-3.5" />
        </CheckboxIndicator>
      </CheckboxRoot>

      <span class="select-none">Select all options</span>
    </label>

    <label class="flex flex-row gap-4 items-center [&>.checkbox]:hover:bg-neutral-100">
      <CheckboxRoot
        v-model:checked="options['1']"
        class="shadow-blackA7 hover:bg-green3 flex h-[25px] w-[25px] appearance-none items-center justify-center rounded-[4px] bg-white shadow-[0_2px_10px] outline-none"
      >
        <CheckboxIndicator class="bg-white h-full w-full rounded flex items-center justify-center">
          <Icon name="radix-icons:check" class="h-3.5 w-3.5" />
        </CheckboxIndicator>
      </CheckboxRoot>

      <span class="select-none">
        Option 1
      </span>
    </label>

    <label class="flex flex-row gap-4 items-center [&>.checkbox]:hover:bg-neutral-100">
      <CheckboxRoot
        v-model:checked="options['2']"
        class="shadow-blackA7 hover:bg-green3 flex h-[25px] w-[25px] appearance-none items-center justify-center rounded-[4px] bg-white shadow-[0_2px_10px] outline-none"
      >
        <CheckboxIndicator class="bg-white h-full w-full rounded flex items-center justify-center">
          <Icon name="radix-icons:check" class="h-3.5 w-3.5" />
        </CheckboxIndicator>
      </CheckboxRoot>

      <span class="select-none">
        Option 2
      </span>
    </label>

    <p class="flex flex-col gap-2">
        <span>Select all: {{ selectAll }}</span>
        <span>Option 1: {{ options['1'] }}</span>
        <span>Option 2: {{ options['2'] }}</span>
    </p>

    <!-- 
        'Select all':
            a. when clicked and unchecked should select all options
            b. when clicked and checked should deselect all options
            c. should get selected when all options get selected
            d. should get deselected when at least one option gets deselected
     -->
  </div>
</template>

<script setup lang="ts">
const selectAll = ref(false)

const options = reactive({
    1: false,
    2: false
})
</script>
