<template>
    <div>
        <ul>
            <li v-for="(customer, index) in customers" :key=index>
                <SingleCustomer :customer="customer" @delete-customer="deleteCustomer(index)"/>
            </li>
        </ul>
        <CustomerForm />
    </div>
</template>

<script>
import {customerService} from '@/services/CustomerService.js'
import SingleCustomer from './SingleCustomer'
import CustomerForm from './CustomerForm'

export default {
    components: {
        SingleCustomer,
        CustomerForm
    },

    data () {
        return {
            customers: customerService.list()
        }
    },

    methods: {
        deleteCustomer(index) {
            console.log(index);
            customerService.remove (this.customers[index])
        }
    }
}
</script>

<style>

</style>
