<template>
  <div class="py-5 border-b border-solid border-brand-gray-2">
    <div
      class="flex flex-wrap items-center justify-between cursor-pointer"
      @click="open"
    >
      <h3 class="text-base font-semibold">{{ header }}</h3>
      <font-awesome-icon :icon="careIcon" />
    </div>

    <div v-if="isOpen" class="w-full mt-5">
      <slot>
        <p>EXAMPLE TEXT</p>
      </slot>
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from "@vue/reactivity";
import { computed, defineComponent } from "@vue/runtime-core";

export default defineComponent({
  name: "Accordion",
  props: {
    header: {
      type: String,
      required: true,
    },
  },
  setup() {
    const isOpen = ref(false);

    const open = () => {
      isOpen.value = !isOpen.value;
    };

    const careIcon = computed(() => {
      return isOpen.value ? ["fas", "angle-up"] : ["fas", "angle-down"];
    });

    return {
      isOpen,

      open,
      careIcon,
    };
  },
});
</script>
