<template>
    <div>
        <input type="text" v-model="search">

        <ul>
            <li v-for="(product, index) in filteredProducts" :key=index>
                {{ product.id }}. {{ product.name }} Quantity: {{ product.quantity}}
                <button @click="handleIncrease(product)">+</button>
                <button @click="handleDecrease(product)">-</button>
                <router-link :to="routeToProduct(product)">
                    <button>Buy</button>
                </router-link>
            </li>
        </ul>
    </div>
</template>

<script>
import {productService} from '@/services/ProductService'

export default {
    data () {
        return {
            products: productService.list(),
            search: ''
        }
    },

    methods: {
        handleIncrease(product){
            productService.increment(product);
        },

        handleDecrease(product){
            productService.decrement(product);
        },

        routeToProduct(product){
            return `/products/${product.id}`
        }
    },

    computed: {
        filteredProducts () {
            return this.products.filter( product => product.name.toLowerCase().includes(this.search.toLowerCase()))
        }
    }
}
</script>

<style>

</style>
