<template>
    <section class="container">
        <div class="row">
            <Search @search="searchCharacter"/>
        </div>
        <div class="row">
            <div class="col-12 col-sm-6 col-lg-3 mb-5" v-for="character in charactersFiltered" :key="character.id">
                <CharacterCard :info="character" :search="searchText"/>
            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import CharacterCard from '../commons/CharacterCard.vue';
import Search from '../commons/Search.vue'
export default {
    name: "CharactersList",
    components: {
        CharacterCard,
        Search
    },
    data() {
        return {
            characters: [],
            searchText: ''
        }
    },
    methods: {
        searchCharacter(payload) {
            this.searchText = payload;
        }
    },
    created() {
        axios.get("https://api.sampleapis.com/rickandmorty/characters")
        .then((response) => {
            this.characters = response.data;
        })
        .catch(function (error) {
            console.log(error);
        });
    },
    computed: {
        charactersFiltered() {
            const array = this.characters.filter(character => {
                if (character.name.toLowerCase().includes(this.searchText.toLowerCase())) {
                    return character;
                }
            });
            return array;
        }
    }
}
</script>

<style lang="scss" scoped>
h2 {
    text-align: center;
}
</style>