<template>
    <JobListings/>
</template>
<script>
import JobListings from '@/components/JobListings.vue';
    export default {
        name: 'JobsView',
        components: {
            JobListings
        },
        setup() {
            return {};
        }
    };
</script>