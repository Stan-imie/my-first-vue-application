<template>
	<div class="hello">
		<ListeAstres :astres="astres"/>
	</div>
</template>

<script>
	import ListeAstres from './ListeAstres.vue';
	export default {
		name: 'HelloWorld',
		components: {
			ListeAstres
		},
		props: {
			msg: String
		},
		data(){
			return{
				astres: []
			}
		},
		created () {
			fetch('https://api.le-systeme-solaire.net/rest/bodies/')
			.then( (data) => data.json())
			.then( (data) => {
				data.bodies.forEach(element => 
					this.astres.push(element)
				);
			});
		}
	}

	

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	h3 {
		margin: 40px 0 0;
	}
	ul {
		list-style-type: none;
		padding: 0;
	}
	li {
		display: inline-block;
		margin: 0 10px;
	}
	a {
		color: #42b983;
	}
</style>
