<template>
    <main>
        <!--richiamo dati da SelectAreaComponent con @selected-->
        <SelectAreaComponent :options="genres" @selected="genreSelected" /> <!--Creo funzione per utilizzare i parametri-->
        <div class="container row">

                                        <!--Sostituisco cdList con FilteredArray per passare i valori selezionati-->
            <div class="d-flex flex-column justify-content-between card" v-for="cd in filteredArray" :key="cd.title">
                <div class="box-card">
                    <img :src="cd.poster" alt="">
                </div>
                <h5>{{ cd.title }}</h5>
                <h6>{{cd.author}} <h6>{{cd.year}}</h6></h6>
                


            </div>

        </div>
    </main>
  
</template>

<script>

import SelectAreaComponent from './SelectAreaComponent.vue';


export default {
name : 'MainComponent',
props : {
    cdList : Array,
},
data(){
    return {
        selected:'',
    }
},
computed:{
    genres(){
        const array = [];
        this.cdList.forEach(element => {
            if(!array.includes(element.genre)){
                array.push(element.genre);
            }
            
        });
       console.log({genres: array})
        return array;
    },
    filteredArray(){  // Creo Array vuoto e per ogni elemento inserisco nel FilteredArray i generi selezionati
        let array = [];
        this.cdList.forEach(item =>{   // cdList Array Totale
            if(item.genre === this.selected){
                array.push(item)
            }
            if(this.selected === ''){
                array = this.cdList  // Nuovo Array = FilteredArray
            }
        })
        return array
    }
    
   

},
components: {
    SelectAreaComponent,
    
},
methods: {
    genreSelected(genres){
        this.selected = genres  //la funzione raccoglie i valori di @selected e li metto in selected=''


    }
        
},
}
</script>

<style lang="scss" scoped>
main {
    background-color: hsl(209deg, 33%, 17%);
}

.container {
    width: 1200px;
    margin: 0 auto;
    padding: 30px 0;

}
.card {
    width: calc(100% / 5 - 40px);
    margin:20px;
    text-align: center;
    height: 350px;
    background-color: hsl(210deg 22% 23%);
    color: white;
    align-items: center;
    padding-top: 15px;

;
    .box-card {
        width: 150px;
        height: 150px;
        
        
    }
}
h6 {
    color: rgb(88, 100, 112);
}

</style>