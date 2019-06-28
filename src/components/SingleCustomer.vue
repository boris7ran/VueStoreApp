<template>
    <div>
        {{ customer.id }}  {{ customer.fullName }}
        <button @click="handleDelete">Delete</button>
    </div>
</template>

<script>
export default {
    props: ['customer'],

    methods: {
        handleDelete () {
            this.$emit('delete-customer')
        }
    }
}
</script>

<style>

</style>
