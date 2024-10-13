<template>
	<main>
		<section class="bg-[#f1f1f1]">
			<div
				class="container flex flex-col lg:flex-row items-center py-20 gap-10"
			>
				<div class="flex-1 order-2 lg:order-1 text-center lg:text-left">
					<h1
						class="text-4xl lg:text-6xl font-extrabold mb-6 text-balance"
					>
						Master the Kitchen with Ease
					</h1>
					<p class="text-base lg:text-xl pb-4">
						Unleash Your Inner Chef Today! Discover recipes helping
						you to find the easiest way to cook.
					</p>
					<button
						class="px-4 py-2 text-white self-start bg-dodgeroll-gold rounded-md text-lg cursor-pointer"
					>
						Browse Recipes
					</button>
				</div>
				<div class="flex-1 order-1 lg:order-2">
					<NuxtImg
						sizes="xs:100vw sm:667px"
						src="/english-breakfast.jpg"
						format="webp"
						densities="x1"
						alt=""
					/>
				</div>
			</div>
		</section>
		<section class="py-20 container">
			<h2 class="text-3xl lg:text-5xl mb-2">Discover, Create, Share</h2>
			<p class="text-base lg:text-xl mb-8">
				Check out our most popular recipes!
			</p>
			<div
				v-if="!error"
				class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6"
			>
				<RecipeCard v-for="recipe in data?.recipes" :recipe="recipe" />
			</div>
			<p v-else class="text-xl">
				Opps, something went wrong. Please try again later
			</p>
		</section>
	</main>
</template>

<script setup lang="ts">
	import RecipeCard from "~/components/RecipeCard.vue";
	import { type RecipeResponse } from "~~/types/types";
	// const { data, error } = await useAsyncData("recipes", () =>
	// 	$fetch("https://dummyjson.com/recipes")
	// );

	const { data, error } = await useFetch<RecipeResponse>(
		"https://dummyjson.com/recipes"
	);

	useSeoMeta({
		title: "Nuxtcipes",
		description: "Recipes for you to cook!",
		ogTitle: "Nuxtcipes",
		ogDescription: "Recipes for you to cook!",
		ogImage: "/nuxt-course-hero.png",
		ogUrl: `http:localhost:3000`,
		twitterTitle: "Nuxtcipes",
		twitterDescription: "Recipes for you to cook!",
		twitterImage: "nuxt-course-hero.png",
		twitterCard: "summary",
	});
</script>
