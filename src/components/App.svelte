<script>
	const getRandomIndex = (maxIndex) => Math.floor(Math.random() * maxIndex)

	const titles = ["Sir", "Mr.", "Admiral", "Captain", "Prince", "King", "Emperor", "Viceroy", "Dr.", "Prof.", "Lieutenant", "Judge", "Governor", "Senator", "Prime-minister", "President", "Marshall"]
	const lastNames = ["Popplewell", "Stevenson", "Svensson", "Honeybottom", "Weaslethorp", "Thistlebob", "Rubricton", "McSybil", "Smarlingrove", "Remingfield", "Carlyle", "Demistroop", "Highwell", "Rovelist", "Ehrmentraut", "von Bismarck", "Knorring", "Wilson", "Markson", "Nichlson"]
	let title = titles[getRandomIndex(titles.length)]
	let fancyLastName = lastNames[getRandomIndex(lastNames.length)]
	let romanNumeral = getRandomIndex(20) + 1

	const getNewBenny = () => {
		title = titles[getRandomIndex(titles.length)]
		fancyLastName = lastNames[getRandomIndex(lastNames.length)]
		romanNumeral = getRandomIndex(20) + 1
	}

	const romanize = (num) => {
		const lookup = {M:1000,CM:900,D:500,CD:400,C:100,XC:90,L:50,XL:40,X:10,IX:9,V:5,IV:4,I:1}
		let	roman = ''
		for ( const i in lookup ) {
			while ( num >= lookup[i] ) {
				roman += i;
				num -= lookup[i];
			}
		}
		return roman;
	}
</script>

<h1>{title} Benedict {fancyLastName} {romanize(romanNumeral)}</h1>
<button on:click={getNewBenny}>New Benny</button>
