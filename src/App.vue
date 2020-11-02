<template>
	<div id="app">
		<Calculator />
	</div>
</template>

<script>
import Calculator from '@/components/Calculator'
export default {
	components: {
		Calculator
	}
}
</script>

<style >
body {
	background-color: #36454d;
	margin: 0;
}
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;

	text-align: center;
	margin-top: 60px;
	/* background-color: #333; */

	width: 300px;
	height: 600px;
	margin: 0 auto;

	border-radius: 6px;
	display: flex;
	flex-wrap: wrap;
	align-content: flex-end;
	justify-content: space-between;
}
</style>
