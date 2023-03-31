<template>
    <h1>{{ greeting }}</h1>
    <h3 class="number">{{ count }}</h3>
    <button class="btn" @click="decCount">-</button>
    <button class="btn" @click="incCount">+</button>
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
        counter: {
            type: Number,
            default: 0,
        }
    },
    data(){
        return {
            greeting: 'Hello!',
            count: 0,
        }
    },
    created() {  
        console.log(this.greeting);
        console.log(this.string);
        console.log('count:',this.count);
    },
    methods: {
        incCount() {
            this.count++;
        },
        decCount() {
            this.count--;
        }
    }
}
</script>

<style>
    .btn {
        margin: 8px;
        padding: 8px 16px;
        border: none;
        background-color: black;
        color: white;
        border-radius: 12px;
        font-size: 20px;
    }
    .btn:hover {
        cursor: pointer;
    }
    .number {
        font-size: 60px;
    }
</style>
