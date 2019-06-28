<template>
    <div>
        <form @submit.prevent="handleAdd">
            <div>
                <label for="fullName">Full Name</label>
                <input type="text" id="fullName" v-model="newCustomer.fullName" required>
            </div>
            <div>
                <label for="email">Email</label>
                <input type="email" id="email" v-model="newCustomer.email" required>
            </div>

            <div>
                <button type="submit">Add Customer</button>
            </div>
        </form>
    </div>
</template>

<script>
import {customerService} from '@/services/CustomerService.js'

export default {
    data () {
        return {
            newCustomer: this.getDefaults()
        }
    },

    methods: {
        getDefaults () {
            return {
                fullName: '',
                email: '',
                products: []
            }
        },

        handleAdd () {
            customerService.add(this.newCustomer);
            this.newCustomer = this.getDefaults;
        }
    }
}
</script>

<style>

</style>
