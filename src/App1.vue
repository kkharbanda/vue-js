<template>
    <div>
        <app-header></app-header>
        <app-profile :alsoKnowAs="name" :lastname="lastname" :age="age" :parents="parents"
            @update-lastname="lastname = $event" @say-hello="alertsay" :updateAge="updateAge"></app-profile>
        <app-footer></app-footer>
    </div>

</template>
<script>
import Profile from './components/User/app-profile.vue';
export default {
    components: {
        'app-profile': Profile
    },
    data() {
        return {
            name: "rocket",
            lastname: "jones",
            age: 12,
            parents: {
                father: "test",
                mother: "hfhjf"
            }

        }
    },
    methods: {
        alertsay() {
            alert("yes");
        },
        updateAge(value){
                this.age = value
            }
    }

}
</script>
<style>
</style>