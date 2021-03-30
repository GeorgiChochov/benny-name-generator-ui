<script>
	import LastNameForm from "./LastNameForm.svelte"
	import TitleForm from "./TitleForm.svelte"

	const getRandomIndex = (maxIndex) => Math.floor(Math.random() * maxIndex)

	const titles = ["Sir", "Mr.", "Admiral", "Captain", "Prince", "King", "Emperor", "Viceroy", "Dr.", "Prof.", "Lieutenant", "Judge", "Governor", "Senator", "Prime-minister", "President", "Marshall"]
	const lastNames = ["Popplewell", "Stevenson", "Svensson", "Honeybottom", "Weaslethorp", "Thistlebob", "Rubricton", "McSybil", "Smarlingrove", "Remingfield", "Carlyle", "Demistroop", "Highwell", "Rovelist", "Ehrmentraut", "von Bismarck", "Knorring", "Wilson", "Markson", "Nichlson"]
	let title = titles[getRandomIndex(titles.length)]
	let fancyLastName = lastNames[getRandomIndex(lastNames.length)]
	let dynasticNumeral = getRandomIndex(20) + 1
	const getPlaceholderBenny = () => {
		return {
			title: titles[getRandomIndex(titles.length)],
			fancyLastName: lastNames[getRandomIndex(lastNames.length)],
			dynasticNumeral: getRandomIndex(20) + 1
		}
	}
	let bennies = [1,2,3,4,5,6,7,8].map(getPlaceholderBenny)
	console.log(bennies)

	const refreshBennies = () => {
		fetch(
			"https://benny-name.herokuapp.com/bennies",
			{
				method: "GET"
			}
		)
			.then(response => response.json())
			.then(data => {
					bennies = data
				}
			)
	}

	let bennyCount = 0
	const getNewBenny = () => {
		if (bennyCount > bennies.length / 2) {
			refreshBennies()
			bennyCount = 0
		}
		bennyCount += 1
		const benny = bennies[getRandomIndex(bennies.length)]
		title = benny.title
		fancyLastName = benny.fancyLastName
		dynasticNumeral = benny.dynasticNumeral
	}

	const romanize = (num) => {
		const lookup = {M: 1000, CM: 900, D: 500, CD: 400, C: 100, XC: 90, L: 50, XL: 40, X: 10, IX: 9, V: 5, IV: 4, I: 1}
		let roman = ""
		for (const i in lookup) {
			while (num >= lookup[i]) {
				roman += i
				num -= lookup[i]
			}
		}
		return roman
	}
</script>

<h1>{title} Benedict {fancyLastName} {romanize(dynasticNumeral)}</h1>
<button on:click={getNewBenny}>New Benny</button>
<LastNameForm/>
<TitleForm/>
