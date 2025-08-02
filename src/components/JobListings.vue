<template>
    <section class="bg-blue-50 px-4 py-10">
        <div class="container-xl lg:container m-auto">
            <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
                Browse Jobs
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <JobListingSingular v-for="job in jobs.slice(0, limit || jobs.length)" :key="job.id" :job="job" />
            </div>
        </div>
    </section>
    <!-- buttın not goes jobs ıdk why stilll show limitid job  -->
    <section v-if="showButton" class="m-auto max-w-lg my-10 px-6">
        <RouterLink to="jobs" class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700">View
            All Jobs</RouterLink>
    </section>
</template>
<script>
import jobData from '@/jobs.json';
import { ref } from 'vue';
import JobListingSingular from './JobListingSingular.vue';
import { RouterLink } from 'vue-router';
export default {
    name: 'JobListings',
    components: {
        JobListingSingular
    },
    props: {
        limit: {
            type: Number,
        },
        showButton: {
            type: Boolean,
            default: false
        }
    },
    setup() {
        const jobs = ref(jobData.jobs)
        // console.log(jobs);

        return {
            jobs
        };
    }
};
</script>