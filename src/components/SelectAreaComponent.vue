<template>
  <div>
    <select name="Select-area" v-model="genres" @change="changeSelect">
        <option value="">All Genres</option>
        <option v-for="option in options" :key="option" :value="option">
            {{option}}
        </option>
        
    </select>
  </div>
</template>

<script>
export default {
name: 'SelectAreaComponent',
data(){
    return {
        genres: ''
    }
  
},
props: {
    options: Array

},
methods: {
    changeSelect(){
        console.log(this.genres)
        this.$emit('selected', this.genres); // Passo gli Elementi a MainComponent con $emit
    }
}

}

</script>

<style lang="scss" scoped>

</style>