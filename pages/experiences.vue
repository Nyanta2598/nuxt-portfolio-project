<script setup>
	import { TransitionRoot } from "@headlessui/vue";
	const isShowing = ref(true);
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
			<div class="relative container mx-auto flex flex-col sm:flex-row gap-16">
				<h1
					class="font-black text-black lg:text-[80px] sm:text-[60px] xs:text-[50px] text-[40px] lg:leading-[98px] mt-2"
				>
					Experiences
				</h1>
			</div>
		</TransitionRoot>
	</section>
</template>
