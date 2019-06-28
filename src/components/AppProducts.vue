<template>
    <div>
        <ul>
            <li v-for="(product, index) in products" :key=index>
                {{ product.id }}. {{ product.name }}
            </li>
        </ul>
    </div>
</template>

<script>
import {productService} from '@/services/ProductService'

export default {
    data () {
        return {
            products: productService.list()
        }
    }
}
</script>

<style>

</style>
