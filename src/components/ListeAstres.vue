<template>

	<div class="ListeAstres">
		<md-table v-model="astres" md-sort="name" md-sort-order="asc" md-card md-fixed-header>
			<md-table-toolbar>
				<div class="md-toolbar-section-start">
				<h1 class="md-title">Astres</h1>
				</div>

				<md-field md-clearable class="md-toolbar-section-end">
				<md-input placeholder="Search by name..." v-model="search" @input="searchOnTable" />
				</md-field>
			</md-table-toolbar>

			<md-table-row slot="md-table-row" slot-scope="{ item }">
				<!-- <md-table-cell md-label="ID" md-sort-by="id" md-numeric>{{ index }}</md-table-cell> -->
				<md-table-cell md-label="Nom" md-sort-by="name">{{ item.name }}</md-table-cell>
				<md-table-cell md-label="English Name" md-sort-by="englishName">{{ item.englishName }}</md-table-cell>
				<md-table-cell md-label="isPlanette" md-sort-by="isPlanet">{{ item.isPlanet }}</md-table-cell>
				<!-- <md-table-cell md-label="Gender" md-sort-by="gender">{{ item.gender }}</md-table-cell>
				<md-table-cell md-label="Job Title" md-sort-by="title">{{ item.title }}</md-table-cell> -->
			</md-table-row>

		</md-table>
	
	</div>



</template>

<script >
	import Vue from 'vue'
	import VueMaterial from 'vue-material'
	import 'vue-material/dist/vue-material.min.css'

	Vue.use(VueMaterial)
	const toLower = text => {
		return text.toString().toLowerCase()
	}
	const searchByName = (items, term) => {
		if (term) {
			return items.filter(item => toLower(item.name).includes(toLower(term)))
	}
	return items
	}

	export default  {
		name: 'ListeAstres',
		props: ['astres'],
		created: function () {
			console.log(this.astres)
			this.searched = this.astres
		},  
		data () {
			return {
				search: null,
				searched: []
			}
		},
		methods: {
			searchOnTable () {
			this.searched = searchByName(this.astres, this.search)
			}
		},
		computed: {

		}
	}

</script>

<style>
	.ListeAstres {
		display: flex;
		justify-content: center;
		/* max-width: 80vh; */
	}
</style>
