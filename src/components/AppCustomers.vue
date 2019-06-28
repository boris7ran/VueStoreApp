<template>
    <div>
        Text
        <ul>
            <li v-for="(customer, index) in customers" :key=index>
                <SingleCustomer :customer="customer" @delete-customer="deleteCustomer"/>
            </li>
        </ul>
    </div>
</template>

<script>
import {customerService} from '@/services/CustomerService.js'
import SingleCustomer from './SingleCustomer'

export default {
    components: {
        SingleCustomer
    },

    data () {
        return {
            customers: customerService.list()
        }
    },

    methods: {
        deleteCustomer(index) {
            customerService.remove (this.customers[index])
        }
    }
}
</script>

<style>

</style>
