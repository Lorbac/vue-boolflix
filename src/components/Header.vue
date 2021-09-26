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

        .search-panel {

            input {
                border-radius: 5px;
                margin: 0 10px;
            }

            button {
                border-radius: 2px;
                border: none;
                padding: 1px 3px;
                font-weight: 600;

                &:active {
                    background-color: rgb(156, 57, 57);
                }
            }
        }
    }
</style>