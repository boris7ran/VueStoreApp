<template>
    <div>
        <div>
            {{ customer.fullName }}
        </div>
        <div>
            <ul>
                <li v-for="(product, index) in customer.products" :key=index>
                    {{ product }}
                </li>  
            </ul>
        </div>
    </div>
</template>

<script>
import {customerService} from '@/services/CustomerService'

export default {

    computed: {
        customer () {
            return customerService.find(this.$route.params.id)
        }
    }
}
</script>

<style>

</style>
