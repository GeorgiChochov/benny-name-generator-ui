<script>
	const getRandomIndex = (maxIndex) => Math.floor(Math.random() * maxIndex)

	const titles = ["Sir", "Mr.", "Admiral", "Captain", "Prince", "King", "Viceroy", "Dr.", "Prof.", "Lieutenant", "Judge", "Governor", "Senator", "Prime-minister", "President", "Marshall"]
	const lastNames = ["Popplewell", "Stevenson", "Svenson", "Honeybottom", "Weaslethorp", "Thistlebob", "Rubricton", "McSybil", "Smarlingrove", "Remingfield", "Carlyle", "Demistroop", "Highwell", "Rovelist"]
	let title = titles[getRandomIndex(titles.length)]
	let fancyLastName = lastNames[getRandomIndex(lastNames.length)]
	let romanNumeral = getRandomIndex(20) + 1

	function romanize(num) {
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

<div class="name-container">
	<h1>{title} Benedict {fancyLastName} {romanize(romanNumeral)}</h1>
</div>
