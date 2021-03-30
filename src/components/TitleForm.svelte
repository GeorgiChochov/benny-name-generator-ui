<script>
	let newTitle = ""
	const submit = () => {
		fetch(
			"https://benny-name.herokuapp.com/titles",
			{
				method: "POST",
				body: newTitle
			}
		)
		newTitle = ""
	}
</script>

<div>
	<label>
		Title
		<input type="text" bind:value={newTitle}/>
	</label>
	<button on:click={submit}>Add</button>
</div>
