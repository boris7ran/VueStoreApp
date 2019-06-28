<template>
    <div>
        {{ product.name }}
        <br/>
        <template v-if="product.quantity">
        <select v-model="customer">
            <option v-for="(customer, index) in customers" :key="index" :value="customer">
                {{ customer.fullName }}
            </option>
        </select>
        <div>
            <button @click="buyProduct">Confirm</button>
            <button @click="cancelBuying">Cancel</button>
        </div>
        </template>
        <template v-else>
            <button @click="cancelBuying">Return to Products</button>
        </template>
    </div>
</template>

<script>
import {customerService} from '@/services/CustomerService.js'
import {productService} from '@/services/ProductService'

export default {
    data() {
        return {
            customer: null,
            customers: customerService.list()
        }
    },

    methods: {
        buyProduct() {
            if (!this.customer){
                alert('Customer not selected!')
            }
            else {
                customerService.addProductToCustomer(this.customer, this.product);
                productService.decrement(this.product);
                this.$router.push(`/customers/${this.customer.id}`)
            }
        },

        cancelBuying(){
            this.$router.push('/products')
        },
    },

    computed: {
        product () {
            return productService.find(this.$route.params.id)
        }
    }
}
</script>

<style>

</style>
