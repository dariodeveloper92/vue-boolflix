<template>
    <form class="d-flex my-5">
        <div class="flex-grow-1">
            <input 
                type="text"
                class="form-control"
                placeholder="Search movie"
                v-model="inputText"
                @keyup.enter="$emit('performSearch', inputText)"
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
    emits:['performSearch'],
    data() {
        return {
            inputText:'',
        }
    },
}
</script>

<style>

</style>