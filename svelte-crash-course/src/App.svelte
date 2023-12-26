<script>
	import FeedbackList from "./components/FeedbackList.svelte";

	let feedbacks = [
		{
			id: 1,
			rating: 10,
			text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam faucibus odio et auctor convallis. Praesent elementum dui quis aliquet ullamcorper. Donec id mi urna. Sed lorem orci, eleifend vel nulla ac, eleifend scelerisque magna. Nullam egestas mollis massa, quis porta tellus ullamcorper non. Nulla euismod velit vel ex rutrum, et."
		},
		{
			id: 2,
			rating: 9,
			text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam faucibus odio et auctor convallis. Praesent elementum dui quis aliquet ullamcorper. Donec id mi urna. Sed lorem orci, eleifend vel nulla ac, eleifend scelerisque magna. Nullam egestas mollis massa, quis porta tellus ullamcorper non. Nulla euismod velit vel ex rutrum, et."
		},
		{
			id: 3,
			rating: 8,
			text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam faucibus odio et auctor convallis. Praesent elementum dui quis aliquet ullamcorper. Donec id mi urna. Sed lorem orci, eleifend vel nulla ac, eleifend scelerisque magna. Nullam egestas mollis massa, quis porta tellus ullamcorper non. Nulla euismod velit vel ex rutrum, et."
		},
	]
</script>

<main>
	<FeedbackList/>
</main>

<style>
</style>