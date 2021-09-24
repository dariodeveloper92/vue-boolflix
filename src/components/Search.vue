<template>
    <form class="d-flex my-5">
        <div class="flex-grow-1">
            <input 
            type="text"
            class="form-control"
            placeholder="Search movie"
            v-model="inputText"
            >
        </div>
        <div class="mx-3">
            <button
                type="submit"
                class="btn btn-danger"
                @click.prevent="$emit('performSearch', inputText)"
            >
                Cerca
            </button>
        </div>
    </form>
</template>

<script>
export default {
    name: 'Search',
    data() {
        return {
            inputText:'',
        }
    },
    methods: {
        
    }
}
</script>

<style>

</style>