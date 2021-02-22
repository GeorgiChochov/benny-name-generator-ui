<script>
	let title = "Sir"
	let fancyLastName = " Popplewell"
	let romanNumeral = 1
	
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
