<template>
	<div class="flex flex-col shadow rounded-md">
		<NuxtImg
			:src="recipe.image"
			format="webp"
			densities="x1"
			alt=""
			class="rounded-t-md aspect-[1/1] object-cover"
		/>
		<div class="flex flex-col py-6 px-4 flex-1">
			<p class="text-xl lg:text-2xl font-semibold mb-2">
				{{ recipe.name }}
			</p>
			<div
				class="font-normal w-full bg-white/80 flex gap-8 text-lg lg:text-xl mb-4 mt-auto"
			>
				<div class="flex items-center gap-1">
					<Icon
						name="mdi:clock-time-eight-outline"
						style="color: #f79f1a"
					/>
					<span class="text-base">{{ recipe.cookTimeMinutes }}</span>
				</div>
				<div class="flex items-center gap-1">
					<Icon name="mdi:fire" style="color: #f79f1a" />
					<span class="text-base">{{
						recipe.caloriesPerServing
					}}</span>
				</div>
				<div class="flex items-center gap-1">
					<Icon name="mdi:star" style="color: #f79f1a" />
					<span class="text-base"
						>{{ recipe.rating }} ({{ recipe.reviewCount }})</span
					>
				</div>
			</div>
			<BaseBtn :to="`/recipes/${recipe.id}`" label="View" />
		</div>
	</div>
</template>

<script setup lang="ts">
	import { type Recipe } from "~~/types/types";

	defineProps<{
		recipe: Recipe;
	}>();
</script>
