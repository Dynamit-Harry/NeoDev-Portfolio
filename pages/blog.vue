<template>
	<div>
		<div class="flex flex-row py-4 px-8">
			<a href="/" class="text-3xl text-white w-1/5"></a>
			<p class="text-white text-3xl text-center w-3/5">Blooug</p>
			<div class="w-1/5"></div>
		</div>
		<div @click="goToPost(post.id)" v-for="post in posts" :key="post.id" class="bg-gray-700 py-4 my-4 mx-8 rounded-xl text-white">
			<div class="ml-4">
				{{ post.title }}
			</div>
			<div class="ml-6">
				{{ post.desc }}
			</div>
		</div>
	</div>
</template>
<script>
	export default {
		name: "IndexPage",
		async asyncData({ $content }) {
			let posts = await $content("BlogPosts").sortBy("CreatedAt", "desc").without(["body"]).fetch();
			return {
				posts,
			};
		},
		methods: {
			goToPost(id) {
				this.$router.push("/BlogPosts/" + id);
			},
		},
	};
</script>
