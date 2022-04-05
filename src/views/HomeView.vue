<script>
import NewsList from '@/components/NewsList.vue'

export default {
    data() {
        return {
            message: "Hello World! Welcome to Onandi's VueJS"
        };
    },
    components: { NewsList }
}
</script>

<template>
    <div class="container">
      <div class="text-center">
        <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />
        <h1>{{ message }}</h1>
        <div class="grid">
          <div class="container_view">
            <NewsList />
          </div>
        </div>
      </div>
    </div>
</template>

<style>
  .container_view {
    max-width: 100%;
    flex-wrap: wrap;
    display: flex;
    justify-content: center;
    align-items: center;
}

</style>