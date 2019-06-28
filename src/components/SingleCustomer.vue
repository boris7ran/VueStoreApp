<template>
    <div>
        {{ customer.id }}  {{ customer.fullName }}
        <button @click="handleDelete">Delete</button>
        <router-link :to="routeToCustomer">
            <button>Latest Purchases</button>
        </router-link>
    </div>
</template>

<script>
export default {
    props: ['customer'],

    methods: {
        handleDelete () {
            this.$emit('delete-customer')
        }
    },

    computed: {
        routeToCustomer () {
            return `/customers/${this.customer.id}`
        }
    }
}
</script>

<style>

</style>
