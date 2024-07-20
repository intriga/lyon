<template>

    <div class="row">
      
        <ThePosts />
        <!-- /col -->
      
        <TheCategories />
        <!-- /aside -->
    </div>
    <!-- /row -->

</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
import ThePosts from '../components/ThePosts.vue'
import PostView from './PostView.vue'
import TheCategories from '../components/TheCategories.vue'
</script>