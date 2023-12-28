<script setup>
	import { TresCanvas } from "@tresjs/core";
	import { OrbitControls } from "@tresjs/cientos";
	import { TransitionRoot } from "@headlessui/vue";
	const isShowing = ref(true);
	const { onLoop } = useRenderLoop();
	const boxRef = shallowRef(null);
	onLoop(({ delta, elapsed }) => {
		// I will run at every frame ~ 60FPS (depending of your monitor)
		if (boxRef.value) {
			// rotate 360° every 4 seconds
			boxRef.value.rotation.y = elapsed;
			boxRef.value.rotation.x = elapsed;
		}
	});
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
			<div class="flex flex-col justify-center items-center p-8 space-y-4">
				<h1
					class="font-black text-black mt-12 md:mt-0 lg:text-[80px] sm:text-[60px] xs:text-[50px] text-[40px] lg:leading-[98px]"
				>
					Full Stack Developer
				</h1>
				<div
					class="relative container mx-auto flex flex-col sm:flex-row gap-4 md:gap-16"
				>
					<div class="w-full sm:w-2/3 text-gray-500 dark:text-light prose">
						<div class="md:w-3/4">
							<h2
								class="text-slate-500 font-medium lg:text-[30px] sm:text-[26px] xs:text-[20px] text-[16px] lg:leading-[40px]"
							>
								Prince Joseph Esteves
							</h2>
							<p class="text-lg py-2">
								Graduated from Bachelor of Science <br />
								in Information Technology
								<br />
								from St. Vincent College of Cabuyao.
							</p>
							<p class="text-lg py-2">
								I'm a software developer with experience in TypeScript and
								JavaScript, and expertise in frameworks like React, and Vue. I'm
								a quick learner and collaborate closely with clients to create
								efficient, scalable, and user-friendly solutions that solve
								real-world problems. Let's work together to bring your ideas to
								life!
							</p>
						</div>
					</div>

					<div
						class="rounded-lg overflow-hidden shadow-lg dark:shadow-gray-700 aspect-1/3 w-full sm:w-1/4 h-96 sm:absolute right-0 top-55%"
					>
						<TresCanvas shadows :clear-color="'#82DBC5'">
							<TresPerspectiveCamera />
							<OrbitControls />
							<Suspense>
								<TresMesh ref="boxRef" :scale="1.6">
									<TresBoxGeometry :args="[1, 1, 1]" />
									<TresMeshNormalMaterial />
								</TresMesh>
							</Suspense>
						</TresCanvas>
					</div>
				</div>
			</div>
		</TransitionRoot>
	</section>
</template>
