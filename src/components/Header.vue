<template>
    <div class="nav-bar">
        <div class="logo">
            <a href="/"><h1>BOOLFLIX</h1></a>
        </div>
        <div class="search-panel">
            <input placeholder="Cerca il tuo film" v-model="inputSearch" type="text" @keydown.enter="$emit('outputSearch', inputSearch)">
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

        a {
            text-decoration: none;
            
            h1 {
                color: red;
                font-weight: 800;
            }
        }

        .search-panel {

            input {
                outline: none;
                border-radius: 5px;
                margin: 0 10px;
                padding: 5px;
            }

            button {
                border-radius: 2px;
                border: none;
                padding: 5px;
                font-weight: 600;
                background-color: red;

                &:active {
                    background-color: rgb(156, 57, 57);
                }
            }
        }
    }
</style>