<template>

    <div class="row">
        <div class="col-lg-9">
            <PostContent />
            <!-- /single-post -->
					
        </div>
        <!-- /col -->
        
        <!-- /col -->
      
        <TheCategories />
        <!-- /aside -->
    </div>
    <!-- /row -->
  
  </template>
  
  <script setup>
  import { RouterLink, RouterView } from 'vue-router'
  import PostContent from '../components/PostContent.vue'
  import TheCategories from '../components/TheCategories.vue'
  </script>