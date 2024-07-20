<template>
    <main>
		<section class="hero_in general">
			<div class="wrapper">
				<div class="container">
					<h1 class="fadeInUp"><span></span>Panagea blog</h1>
				</div>
			</div>
		</section>
		<!--/hero_in-->

		<div class="container margin_60_35">
			<div class="row">
				
                <ThePosts />
				<!-- /col -->
				
                <TheCategories />
				<!-- /aside -->
			</div>
			<!-- /row -->
		</div>
		<!-- /container -->
	</main>
</template>
<script setup>
import { RouterLink, RouterView } from 'vue-router'
import ThePosts from './ThePosts.vue'
import TheCategories from './TheCategories.vue'
</script>