<template>
    <div id="page">
		
	<header class="header menu_fixed">
		<div id="preloader"><div data-loader="circle-side"></div></div><!-- /Preload -->
		<div id="logo">
			<a href="index.html">
				<img src="../public/img/logo.svg" width="150" height="36" alt="" class="logo_normal">
				<img src="../public/img/logo_sticky.svg" width="150" height="36" alt="" class="logo_sticky">
			</a>
		</div>
		<ul id="top_menu">
			<li><a href="cart-1.html" class="cart-menu-btn" title="Cart"><strong>4</strong></a></li>
			<li><a href="#sign-in-dialog" id="sign-in" class="login" title="Sign In">Sign In</a></li>
			<li><a href="wishlist.html" class="wishlist_bt_top" title="Your wishlist">Your wishlist</a></li>
		</ul>
		<!-- /top_menu -->
		<a href="#menu" class="btn_mobile">
			<div class="hamburger hamburger--spin" id="hamburger">
				<div class="hamburger-box">
					<div class="hamburger-inner"></div>
				</div>
			</div>
		</a>
		<nav id="menu" class="main-menu">
			<ul>
				<li><span><RouterLink to="/">Home</RouterLink></span></li>
				<li><span><RouterLink to="/about">About</RouterLink></span></li>
				<li><span><RouterLink to="/contact">Contact</RouterLink></span></li>
				
			</ul>
		</nav>

	</header>
	<!-- /header -->
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
			

			<RouterView />
			
			
		</div>
		<!-- /container -->
	</main>
	<!--/main-->
	
	<TheFooter />
	<!--/TheFooter.vue-->
	</div>
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
import TheMain from './components/TheMain.vue'
import PostView from './views/PostView.vue'
import TheFooter from './components/TheFooter.vue'
</script>