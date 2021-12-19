<template>
    <div class="search-section mb-5">
        <div class="search-bar me-5">
            <input type="text" placeholder="Search for a character" v-model="searchText" @keyup.enter="$emit('search', searchText)">
        </div>
        <button class="btn btn-primary me-2 search" @click="$emit('search', searchText)">Search</button>
        <button class="btn btn-warning reset" @click="$emit('search', '')">Reset</button>
    </div>
</template>

<script>
export default {
    name: "Search",
    data() {
        return {
            searchText: "",
        }
    }
}
</script>

<style lang="scss" scoped>
.search-section {
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>