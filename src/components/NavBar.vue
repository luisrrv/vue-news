<template >
    <nav class="navbar">
        <h3>{{title}}</h3>
        <input type="text" name="search" id="search" placeholder="Search">
    </nav>
</template>

<script>
export default {
    name: 'NavBar',
    props: {
        msg: String,
        // title: {
        //     type: String,
        //     required: true,
        //     default: 'Hello!'
        // }
    },
    data(){
        return {
            title: 'Vue Counter'
        }
    },
    created() {
        console.log('title:',this.title)
    }
}
</script>

<style>
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 30px;
    padding: 0 20px;
}
.navbar input {
    border-radius: 20px;
    border: none;
    padding: 12px 16px;
    background-color: black;
    color: white;
}
::placeholder {
  color: white;
  opacity: 1; /* Firefox */
}
</style>