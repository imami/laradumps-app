<template>
    <div v-if="props.payload.validate_json">
        <div class="flex w-full left-0 items-center p-2">
            <div
                class="items-center w-[0.50rem] h-[0.50rem] mr-2 rounded-full"
                :class="{ [style]: true }"
            ></div>
            <span class="flex gap-2 dark:text-slate-300 text-sm">{{ $t(text) }}</span>
        </div>
    </div>
</template>

<script setup lang="ts">
import { computed, defineProps } from "vue";
import { Payload } from "@/types/Payload";

const style = computed(() => (props.payload.is_json ? "bg-green-500" : "bg-red-500"));

const text = computed(() => (props.payload.is_json ? "valid_json_format" : "invalid_json_format"));

const props = defineProps<{
    payload: Payload;
}>();
</script>

<style>
.vjs-tree {
    @apply !pl-4;
}
.vjs-tree-brackets {
    @apply dark:text-slate-400;
}
.vjs-carets {
    @apply dark:text-slate-400;
}
.vjs-tree-node.is-highlight,
.vjs-tree-node:hover {
    @apply bg-transparent;
}

.vjs-tree-node .vjs-indent-unit.has-line {
    @apply dark:border-l-slate-700;
}
</style>
