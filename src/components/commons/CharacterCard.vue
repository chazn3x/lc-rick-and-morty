<template>
    <div class="character text-center">
        <img class="w-100 mb-3" :src="info.image" :alt="info.name + ' avatar'">
        <h4>{{info.name}}</h4>
        <hr class="mx-auto">
        <p>{{info.origin}}</p>
        <p><strong>{{info.species}}</strong></p>
    </div>
</template>

<script>
export default {
    name: "CharacterCard",
    props: {
        info: Object
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
}
</style>