<template>
    <div>
        <h3>Selecteer uw hond</h3>
        <select name="" id="" v-model="selectedDog" v-on:change="gebeurtenis(selectedDog)" >
            <option value="" disabled selected>Selecteer een hond</option>
            <option v-for="dog in dogs">{{dog}}</option>
        </select>
    </div>
</template>

<script>
    export default {
    	name: "dogSelector",
        data() {
	        return {
		        berend: "meneer",
                selectedDog: null
	        }
        },
          methods: {
                gebeurtenis(input){
                    console.log('er zijn gebeurtenissen');
                    console.log(input);

                    this.$emit('childChanged', input);
                }
          },
        props: ["dogs"]
    }
</script>

<style>
</style>