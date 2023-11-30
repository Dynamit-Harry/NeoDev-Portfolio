<template>
	<div>
		<p class="text-md text-white italic pt-8 pl-24"><Strong class="text-2xl text-purple-700">Hey! </Strong>I'm Neo Fors, a student at Hitatchigymnasiet in vasteras, sweden (Västerås)</p>
		<p class="text-white pt-4 pl-24 text-xl">Some things I've created:</p>
		<div class="flex flex-row justify-between px-16">
			<div class="flex flex-col place-self-start place-content-center w-7/12 text-center">
				<div class="flex text-start flex-col py-4 text-white border-gray-900 shadow-2xl rounded-2xl bg-gray-800 mx-4 my-4" v-for="project in projects" :key="project.id">
					<a :href="project.url">
						<h1 class="text-xl pl-4 overflow-hidden">{{ project.id }} {{ project.title }}</h1>
						<p class="px-8 overflow-hidden">{{ project.desc }}</p>
					</a>
				</div>
			</div>
			<div class="flex flex-col align-self-center place-self-start place-content-center shadow-2xl w-3/12 bg-gray-800 rounded-3xl">
				<p class="flex self-center text-white border-purple-700 border-b-2 my-2">About me</p>
				<div class="text-center py-2 px-8 text-white overflow-hidden" v-for="info in me_info" :key="info.id">
					{{ info.info }}
				</div>
				<div class="flex flex-row justify-between">
					<a href="/PlaceholderCV.doc" class="text-white mb-4 mt-4 p-2 rounded-2xl bg-gray-600 hover:bg-gray-700 ml-16">Get My CV</a>
					<a href="/blog" class="mb-4 mt-4 p-2 text-white rounded-2xl bg-gray-600 hover:bg-gray-700 mr-16">Blog</a>
				</div>
			</div>
		</div>
		<div class="pb-16">
			<p class="text-white pt-4 pl-24 text-xl">Some things I've contributed to:</p>
			<div></div>
		</div>
	</div>
</template>

<script>
	export default {
		name: "IndexPage",
		async asyncData({ $content }) {
			let projects = await $content("../content/projects").sortBy("id", "asc").without(["body"]).fetch();
			return {
				projects,
			};
		},
		data() {
			return {
				links: [
					{ id: 1, url: "https://github.com/Peach-Iced-Tea", title: "Private Github" },
					{ id: 2, url: "https://github.com/Dynamit-Harry", title: "School Github" },
					{ id: 3, url: "https://www.instagram.com/neo_f_05/", title: "Instagram" },
				],
				me_info: [
					{ id: 1, info: "School: Hitatchigymnasiet Vasteras" },
					{ id: 2, info: "Age: 18" },
					{ id: 3, info: "Languages: python, html, javascript, css, c++, c#" },
					{ id: 4, info: "Frameworks: Vue, Nuxt, Quasar" },
					{ id: 5, info: "Interests: Space, AI, Gaming, Deep Learning, fusion/fission, coding( primarily python )" },
				],
			};
		},
		methods: {},
	};
</script>
