<template>
    <section class="bg-blue-50 px-4 py-10">
        <div class="container-xl lg:container m-auto">
            <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
                Browse Jobs
            </h2>
            <!-- show loading spinner while loading is true -->
            <div v-if="state.isLoading" class="text-center text-gray-500 py-6">
                <PulseLoader />
            </div>
            <!-- show job listing when done loading -->
            <div v-else class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <JobListingSingular v-for="job in state.jobs.slice(0, limit || state.jobs.length)" :key="job.id" :job="job" />
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
import { reactive, ref, onMounted } from 'vue';
import JobListingSingular from './JobListingSingular.vue';
import { RouterLink } from 'vue-router';
import axios from 'axios';
import PulseLoader from 'vue-spinner/src/PulseLoader.vue';

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
        const state = reactive({
            jobs: [],
            isLoading: true
        })
        // console.log(jobs);

        onMounted(async () => {
            try {
                const response = await axios.get('http://localhost:5000/jobs'); // Replace with your API endpoint
                state.jobs = response.data;
            } catch (error) {
                console.error('Error fetching jobs:', error);
            } finally {
                state.isLoading = false;
            }
        });
        return {
            state
        };
    }
};
</script>