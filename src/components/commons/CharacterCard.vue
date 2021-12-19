<template>
    <div class="character text-center">
        <img class="w-100 mb-3" :src="info.image" :alt="info.name + ' avatar'">
        <h4 v-if="search.length == 1">
            <span v-for="(part, index) in info.name" :key="index"><span :class="{'text-warning': part.toLowerCase() == search.toLowerCase()}">{{part}}</span></span>
        </h4>
        <h4 v-else>
            <span v-for="(part, index) in filteredName" :key="index"><span :class="{'text-warning': part.toLowerCase() == search.toLowerCase()}">{{part}}</span></span>
        </h4>
        <hr class="mx-auto">
        <p>{{info.origin}}</p>
        <p><strong>{{info.species}}</strong></p>
    </div>
</template>

<script>
export default {
    name: "CharacterCard",
    props: {
        info: Object,
        search: String
    },
    computed: {
        filteredName() {
            let name = this.info.name.toLowerCase().split(`${this.search.toLowerCase()}`);
            if (this.info.name.toLowerCase().includes(this.search.toLowerCase())) {
                name.splice(1, 0, this.search.toLowerCase());
            }
            return name;
        }
    }
}
</script>

<style lang="scss" scoped>
.character {
    img {
        border-radius: 50%;
        box-shadow: 0 0 .5rem lightgrey;
    }
    hr {
        width: 60px;
        opacity: 1;
    }
    h4 {
        text-transform: capitalize;
    }
}
</style>