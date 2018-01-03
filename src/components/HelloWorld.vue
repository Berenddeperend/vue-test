<template>
    <div>
        <dog-selector v-bind:dogs="dogs" v-on:childChanged="childUpdated"></dog-selector>

        <div v-if="selectedDog">
            <p >Geselecteerde hond:</p>
            <h4>{{selectedDog}}</h4>
        </div>

    </div>
</template>

<script>
    import axios from "../../node_modules/axios";
    import DogSelector from "./dogSelector";

    export default {
      components: {DogSelector},
	  name: 'HelloWorld',
	  data () {
        return {
		  msg: 'Welcome to Your Vue.js App',
          dogs: {},
          selectedDog: null
		}
	  },
      methods: {
      	childUpdated(dog) {
      		this.selectedDog = dog;
        }
      },
	  created() {
          axios.get('https://dog.ceo/api/breeds/list/all').then(response => {
          	this.dogs = Object.keys(response.data.message);
          });
      }
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h1, h2 {
      font-weight: normal;
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