<template>
    <div class="counter">
        <h3 class="number">{{ count }}</h3>
        <button class="btn" @click="decCount">-</button>
        <button class="btn" @click="incCount">+</button>
    </div>
</template>

<script>
export default {
    name: 'CounterComp',
    props: {
        msg: String,
        string: {
            type: String,
            required: true
        },
    },
    data(){
        return {
            count: 0,
        }
    },
    created() {  
        // console.log(this.greeting);
        // console.log(this.string);
        // console.log('count:',this.count);
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

<style lang="scss">
@import "../styles/_variables.scss";
    .btn {
        margin: 8px;
        padding: 8px 16px;
        border: none;
        background-color: $white;
        color: $black;
        border-radius: 12px;
        font-size: 20px;
        min-width: 50px;
    }
    .btn:hover {
        cursor: pointer;
    }
    .number {
        font-size: 60px;
        color: $white;
    }
</style>
