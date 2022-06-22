<template>
    <div>
        {{ alsoKnowAs }}
        {{ lastname }}
        {{ age }}
        <ul>
            <li v-for="(key, value, index) in parents" :key="index">
                {{ value }}-{{ key }}
            </li>
        </ul>

        <button @click="updatelastanme">Update last name</button>
        
        <button @click="sayalert">alert way</button>
        <button @click="updateAge(40)">Update age</button>
    </div>
</template>
<script>


export default {
    props: {
        alsoKnowAs: {
            type:String,
            required :true,
            default:'N/A'
        },
        lastname: {type:String,
        validator(value){
                    if(value === 'jones'){
                        return true
                    }else{
                        return false
                    }
                }},
        age: [Number,String],
        parents: Object,
        updateAge : Function
    },emits:{
            'update-lastname':function(lastname){
                if(lastname === 'Michelson'){
                    return true;
                } else {
                    alert('Wrong value dev !!')
                    return false
                }
            }
        },
    data() {
        return {
            name: 'Steve'
        }
    },
    methods: {
        updatelastanme() {
            this.$emit('update-lastname', 'michel')
        },
        sayalert(){
            this.$emit('say-hello')
        }
    }

}
</script>
<style scoped>
div {
    color: burlywood;
}
</style>