<template>

    <div class="row">
        
            <PostsByCategory />
            <!-- /single-post -->
					
        
        <!-- /col -->
        
        <!-- /col -->
      
        <TheCategories />
        <!-- /aside -->
    </div>
    <!-- /row -->
  
  </template>
  
  <script setup>
  import { RouterLink, RouterView } from 'vue-router'
  import PostsByCategory from '../components/PostsByCategory.vue'
  import TheCategories from '../components/TheCategories.vue'
  </script>