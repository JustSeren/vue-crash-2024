<template>
    <div :class="`${bg} p-6 rounded-lg shadow-md`">
        <slot></slot>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        bg: {
            type: String,
            default: 'bg-gray-100'
        },
    },
    setup() {
        return {};
    }
};
</script>