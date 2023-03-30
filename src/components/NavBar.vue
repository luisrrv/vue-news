<template>
    <h1>{{ greeting }}</h1>
</template>

<script>
export default {
    name: 'NavBar',
    props: {
        msg: String,
        string: {
            type: String,
            required: true
        },
        age: {
            type: Number,
            default: 20,
        }
    },
    data(){
        return {
            greeting: 'Hello!',
        }
    },
    created() {  
        console.log(this.greeting);
        console.log(this.string);
        console.log(this.age);
    }
}
</script>
