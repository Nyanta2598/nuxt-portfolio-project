<script setup>
	import { TransitionRoot } from "@headlessui/vue";
	const isShowing = ref(true);
	const projects = ref([
		{
			id: 1,
			name: "vue-tresjs",
			description: "Vue 3 integration for Tres.js",
			url: "",
			totalCount: 0,
			stargazers: {
				totalCount: 1,
			},
			forks: {
				totalCount: 1,
			},
			watchers: {
				totalCount: 1,
			},
		},
		{
			id: 2,
			name: "vue-tresjs",
			description: "Vue 3 integration for Tres.js",
			url: "",
			stargazers: {
				totalCount: 1,
			},
			forks: {
				totalCount: 1,
			},
			watchers: {
				totalCount: 1,
			},
		},
	]);
</script>
<template>
	<section class="min-h-screen flex flex-col justify-center">
		<TransitionRoot
			appear
			:show="isShowing"
			enter="transform transition ease-in-out duration-[300ms] transform"
			enter-from="opacity-0 -translate-x-1/4"
			enter-to="opacity-100 translate-x-0"
			leave="transition ease-in-out duration-[400ms] transform"
			leave-from="translate-x-0"
			leave-to="-translate-x-full"
		>
			<h1
				class="font-black text-black lg:text-[80px] sm:text-[60px] xs:text-[50px] text-[40px] lg:leading-[98px] mt-2"
			>
				Projects
			</h1>

			<p
				class="text-slate-500 font-medium lg:text-[30px] sm:text-[26px] xs:text-[20px] text-[16px] lg:leading-[40px]"
			>
				Here are some of my projects on GitHub.
			</p>
			<div
				class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4"
			>
				<div
					v-for="project in projects"
					:key="project.id"
					class="p-8 border-4 rounded-lg hover:bg-gray-50"
				>
					<a :href="project.url" target="_blank">
						<h2
							class="text-2xl text-indigo-800 font-semibold mb-2 hover:underline"
						>
							{{ project.name }}
						</h2>
					</a>
					<p>{{ project.description }}</p>
					<div class="mt-4">
						<Icon name="fontisto:star" size="1.1rem" class="text-indigo-700" />
						Stars: {{ project.stargazers.totalCount }}
						<Icon
							name="system-uicons:branch"
							size="1.1rem"
							class="text-indigo-800"
						/>
						Forks: {{ project.forks.totalCount }}
						<Icon
							name="system-uicons:eye"
							size="1.1rem"
							class="text-indigo-700"
						/>
						Watchers: {{ project.watchers.totalCount }}
					</div>
				</div>
			</div>
		</TransitionRoot>
	</section>
</template>
