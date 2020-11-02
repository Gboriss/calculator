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
	<button 
		class="btn operator"
		@click="divide"
	>÷</button>
	<button 
		class="btn"
		@click="append('7')"
	>7</button>
	<button 
		class="btn"
		@click="append('8')"
	>8</button>
	<button 
		class="btn"
		@click="append('9')"
	>9</button>
	<button 
		class="btn operator"
		@click="times"
	>x</button>
	<button 
		class="btn"
		@click="append('4')"
	>4</button>
	<button 
		class="btn"
		@click="append('5')"
	>5</button>
	<button 
		class="btn"
		@click="append('6')"
	>6</button>
	<button 
		class="btn operator"
		@click="minus"
	>-</button>
	<button 
		class="btn"
		@click="append('1')"
	>1</button>
	<button 
		class="btn"
		@click="append('2')"
	>2</button>
	<button 
		class="btn"
		@click="append('3')"
	>3</button>
	<button 
		class="btn operator"
		@click="add"
	>+</button>
	<button 
		class="btn zero"
		@click="append('0')"
	>0</button>
	<button 
		class="btn"
		@click="dot"
	>,</button>
	<button 
		class="btn operator"
		@click="equally"
	>=</button>
</div>
</template>

<script>
export default {
	data() {
		return {
			current: '',
			operator: null,
			previous: null,
			operatorClicked: false
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
		append(number) {
			if (this.operatorClicked) {
				this.current = ''
				this.operatorClicked = false
			}
			this.current = this.current + number
		},
		dot() {
			if (this.current.indexOf(',') === -1 ) {
				this.append(',')
			}
		},
		setPrevious() {
			this.previous = this.current
			this.operatorClicked = true
		},
		divide() {
			this.operator = (a, b) => a / b
			this.setPrevious()
		},
		times() {
			this.operator = (a, b) => a * b
			this.setPrevious()
		},
		minus() {
			this.operator = (a, b) => a - b
			this.setPrevious()
		},
		add() {
			this.operator = (a, b) => a + b
			this.setPrevious()
		},
		equally() {
			this.current = this.operator(parseFloat(this.previous), parseFloat(this.current))
			this.previous = null
		}
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