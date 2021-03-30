<script>
	let newLastName = ""
	const submitName = () => {
		fetch(
			"https://benny-name.herokuapp.com/last-names",
			{
				method: "POST",
				body: newLastName
			}
		)
		newLastName = ""
	}
</script>

<div>
	<label>
		Fancy Last Name
		<input type="text" bind:value={newLastName}/>
	</label>
	<button on:click={submitName}>Add</button>
</div>
