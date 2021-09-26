<template>
    <div class="nav-bar">
        <div class="logo">
            <h1>BOOLFLIX</h1>
        </div>
        <div class="search-panel">
            <input v-model="inputSearch" type="text" @keydown.enter="$emit('outputSearch', inputSearch)">
            <button @click.prevent="$emit('outputSearch', inputSearch)">
                Cerca
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            inputSearch: "",
        }
    }
}
</script>

<style scoped lang="scss">

    .nav-bar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        height: 80px;
        background-color: black;
        padding: 0 30px;

        h1 {
            color: red;
        }
    }
</style>