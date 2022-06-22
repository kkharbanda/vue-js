<template>
    <div>
        <order></order>
    </div>

</template>
<script>
import order from './components/orders/app-index.vue'
export default{
    components:{
        order
    },
data(){
   return{
    orders :[
        {"name":"order1","price":"100"},
        {"name":"order12","price":"200"}
    ]
   } 
},
provide(){
            return {
                orders: this.orders,
                changeOrder: this.changeOrder
            }
        },
methods:{
            changeOrder(){
                this.orders[0].price = 'Renault'
            }
        }
}
</script>
<style>
</style>