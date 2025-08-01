<template>
    <Hero title="Test Title" subtitle="Test Subtitle" />
    <HomeCards />
    <JobListings :limit="3" :showButton="true" />
</template>
<script>
import Hero from '@/components/Hero.vue';
import HomeCards from '@/components/HomeCards.vue';
import JobListings from '@/components/JobListings.vue';
export default {
    name: 'HomeView',
    components: {
        Hero,
        HomeCards,
        JobListings
    },
    setup() {
        return {};
    }
};
</script>