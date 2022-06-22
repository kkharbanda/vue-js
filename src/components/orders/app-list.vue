<template>
    <div>
        <ul>
            <li v-for="order in orders" :key="order.name">
                <span>{{ order.price}}</span>:{{order.name }}
            </li>
        </ul>
         <button @click="changeOrder">change order</button>
    </div>
</template>

<script>
export default {
  inject:['orders','changeOrder'],
    data(){
        return {
        }
    }
}
</script>