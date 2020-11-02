<template>
<div class="calculator">
	<div class="display">{{ current || '0'}}</div>
	<button 
		class="btn grey"
		@click="clear"
	>C</button>
	<button 
		class="btn grey"
		@click="sign"
	>+/-</button>
	<button 
		class="btn grey"
		@click="percent"
	>%</button>
	<button class="btn operator">÷</button>
	<button 
		class="btn"
	>7</button>
	<button 
		class="btn"
	>8</button>
	<button 
		class="btn"
	>9</button>
	<button class="btn operator">x</button>
	<button 
		class="btn"
	>4</button>
	<button 
		class="btn"
	>5</button>
	<button 
		class="btn"
	>6</button>
	<button class="btn operator">-</button>
	<button 
		class="btn"
	>1</button>
	<button 
		class="btn"
	>2</button>
	<button 
		class="btn"
	>3</button>
	<button class="btn operator">+</button>
	<button 
		class="btn zero"
	>0</button>
	<button class="btn">,</button>
	<button class="btn operator">=</button>
</div>
</template>

<script>
export default {
	data() {
		return {
			current: '',
		}
	},
	methods: {
		clear() {
			this.current = ''
		},
		sign() {
      		this.current = this.current.charAt(0) === '-' ? 
        	this.current.slice(1) : `-${this.current}`
		},
		percent() {
      		this.current = `${parseFloat(this.current) / 100}`
		},
	}

}
</script>

<style scoped lang="scss">
.calculator {
	display: grid;
	// grid-template-columns: repeat(4, 1fr);
	grid-auto-rows: minmax(50px, auto);
	color: white;

	font-size: 40px;
	background-color: #171616;
	border-radius: 6px;
}
.display {
	display: flex;
	align-items: center;
	justify-content: flex-end;
	grid-column: 1 / 5;
	background-color: #171616;
	color: white;
	border-radius: 10px;
	
	height: 110px;
	
	padding: 0 5px;
	pointer-events: none;
}
.zero {
	grid-column: 1 / 3;
	width: 145px;
	border-radius: 32px;
}


.btn {
	background-color: #333;
	border: 1px solid #363535;
}
.operator {
	background-color: #FE9400;
	color: white;
}
.grey {
	background-color: #A5A5A5;
	color: #111;

}

button {
	font-family: inherit;
	background-color: transparent;
	color: inherit;
	border: none;
	padding: 0;
	border-radius: 0;
	outline: none;	
	cursor: pointer;

	width: 64px;
	height: 64px;
	border-radius: 50%;
	margin: 5px;
	font-size: 24px;
	text-transform: uppercase;
	transition: transform .2s;
	&:active {
		transform: translate3d(0, 2px, 0);
	}
}

</style>