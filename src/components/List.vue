<template>
  <div id="list">
			<div class="list__cow" v-for="cow in cows" :key="cow.name">
				<p class="list__cow__name">{{cow.name}}</p>
				<p>Hunger: {{cow.hunger}}</p>
				<img src="@/assets/hearts/fullHeart.png" v-for="n in hearts(cow.hunger).fullHearts" :key="'hap_full' + cow.name + n">
				<img src="@/assets/hearts/halfFullHeart.png" v-if="hearts(cow.hunger).halfFullHearts">
				<img src="@/assets/hearts/emptyHeart.png" v-for="n in hearts(cow.hunger).emptyHearts" :key="'hap_empty' + cow.name + n">
				<p>Happiness: {{cow.happiness}}</p>
				<img src="@/assets/hearts/fullHeart.png" v-for="n in hearts(cow.happiness).fullHearts" :key="'hun_full' + cow.name + n">
				<img src="@/assets/hearts/halfFullHeart.png" v-if="hearts(cow.happiness).halfFullHearts">
				<img src="@/assets/hearts/emptyHeart.png" v-for="n in hearts(cow.happiness).emptyHearts" :key="'hun_empty' + cow.name + n">
				<p>Energy: {{cow.energy}}</p>
				<img src="@/assets/hearts/fullHeart.png" v-for="n in hearts(cow.energy).fullHearts" :key="'eng_full' + cow.name + n">
				<img src="@/assets/hearts/halfFullHeart.png" v-if="hearts(cow.energy).halfFullHearts">
				<img src="@/assets/hearts/emptyHeart.png" v-for="n in hearts(cow.energy).emptyHearts" :key="'eng_empty' + cow.name + n">
			</div>
  </div>
</template>

<script>


export default {
  name: 'List',
  components: {
		
	},
	props: {
		cows: Array
	},
	data () {
		return {
			
		}
	},
	methods: {
		hearts (statValue) {
			const heartScale = Math.round(statValue/10)
			let hearts = {
				fullHearts: Math.floor(heartScale/2),
				halfFullHearts: heartScale % 2,
				emptyHearts: 5 - Math.floor(heartScale/2) - heartScale % 2
			}
			return hearts
		}
	},
	computed: {
	
	}
}
</script>

<style scoped>
#list {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
	position: absolute;
	height: 90%;
	right: 0;
	background-color: beige;
	width: 10%;
	color: black;
	padding: 10px;
	overflow-y: scroll;
}

.list__cow {
	margin-bottom: 25px;
}

.list__cow__name {
	font-weight: 700;
}

</style>
