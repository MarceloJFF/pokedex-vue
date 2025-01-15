<script setup>

import { onMounted, ref } from 'vue';

let vetor = ref([])

let carregamento = ref(true)

let termoFiltragem = ref('')

onMounted(async ()=>{
    for(let indice =152; indice <= 251; indice++){
        let requisicao = await fetch('https://pokeapi.co/api/v2/pokemon/'+indice)
        let pokemon = await requisicao.json()
        console.log(pokemon)
        vetor.value.push(pokemon)
        
    }
    carregamento.value = false
})

    function filtrar(){
        return vetor.value.filter(obj => obj.name.toLowerCase().includes(termoFiltragem.value.toLowerCase()));
    }

</script>


<template>
    
    <div class="container carregamento" v-if="carregamento">
        <img src = "../complementos/carregamento.gif">
    </div>

    <main class="container" v-if="!carregamento">
        <div class="row">
            <div class="col-12">
                <input type="text"  v-model="termoFiltragem" placeholder="Qual pokemon você está procurando?" class="form-control m-2">
                <p v-if="filtrar().length == 0"> Não foi encontrado nenhum pokemon.</p>
                <p v-else-if="filtrar().length==1 " >Foi encontrado apenas um Pokemon.</p>
                <p v-else> Foram encontrados {{ filtrar().length }} Pokemons.</p>
            </div>

        </div>

        <div class="row">
            <div class="col-12 col-sm-6 col-md-4 col-lg-3" v-for="v in filtrar()">
                <div class="card p-2" :class="v.types[0].type.name" >
                    <img :src="v.sprites.other.home.front_default">
                    <p>{{ v.name }}</p>
                </div>
            </div>

        </div>
    </main>
</template>