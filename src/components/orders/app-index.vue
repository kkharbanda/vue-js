<template>
    <div>
        <h1>Welcome to the orders</h1>
        <div>
            <comp-list></comp-list>
        </div>
    </div>
</template>

<script>
import compList from './app-list.vue';
export default {
    props:['orders'],
    components:{
        compList
    },
    data(){
        return {
        }
    }
}
</script>