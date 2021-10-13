<template>
	<div id="app">
		<div id="nav"><a href="http://localhost:8888/" target="_blank">app</a> |</div>
		<router-view />
	</div>
</template>

<script>
export default {
	data() {
		return {
			parametros: null,
			token: this.parametros.access_token,
		};
	},
	methods: {
		getHashParams() {
			var hashParams = {};
			var e,
				r = /([^&;=]+)=?([^&;]*)/g,
				q = window.location.hash.substring(1);
			while ((e = r.exec(q))) {
				hashParams[e[1]] = decodeURIComponent(e[2]);
			}
			this.parametros = hashParams;
			console.log(this.parametros);
			console.log(this.token);
		},
	},
	created() {
		this.getHashParams();
	},
};
</script>

<style lang="scss">
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
}

#nav {
	padding: 30px;

	a {
		font-weight: bold;
		color: #2c3e50;

		&.router-link-exact-active {
			color: #42b983;
		}
	}
}
</style>
