<template>
    <a :href="href" target="_blank"
        class="px-3 py-2 rounded border-2 border-orange-600 bg-orange-600 hover:bg-orange-600 text-white transition-colors">
        <slot>Youtube</slot>
    </a>
</template>

<script setup>
const props = defineProps({
    href: String
})

</script>