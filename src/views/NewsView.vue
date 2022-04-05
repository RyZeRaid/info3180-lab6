<template>
    <div class="news container">
        <div class="text-container">
            <h2>News</h2>
            <NewsList />
        </div>
    </div>
</template>

<script>
    import NewsList from '@/components/NewsList.vue'

    export default {
    data() {
    return {};
    },
    components: { NewsList }
    };
</script>