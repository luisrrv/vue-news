
<template >
    <nav class="navbar">
        <div class="top">
            <h3>{{title}}</h3>
            <div class="right">
                <template v-if="isLightMode">
                    <DarkIcon type="mdi" :path="path" title="dark mode" fillColor="#eeeeee" size="24" @click="toggleMode" />
                </template>
                <template v-else>
                    <LightIcon type="mdi" :path="path" title="light mode" fillColor="#eeeeee" size="24" @click="toggleMode" />
                </template>
                <div class="menu">
                    <MenuIcon title="menu" size="30" @click="toggleMode" />
                    <div class="menu-list">
                        <p>Login</p>
                    </div>
                </div>
            </div>
        </div>
        <input class="search" type="text" name="search" id="search" placeholder="Search" v-model="query" @keyup="onKeyUp">
    </nav>
</template>

<script>
import MenuIcon from 'vue-material-design-icons/Menu.vue';
import LightIcon from '@jamescoyle/vue-icon';
import { mdiWhiteBalanceSunny } from '@mdi/js';
import DarkIcon from '@jamescoyle/vue-icon';
import { mdiWeatherNight } from '@mdi/js';
export default {
    name: 'NavBar',
    components: {
        MenuIcon,
        LightIcon,
        DarkIcon,
    },
    props: {
        msg: String,
    },
    data(){
        return {
            title: 'News Feed',
            path: this.isLightMode ? mdiWeatherNight : mdiWhiteBalanceSunny,
            isLightMode: false,
            searchTimer: null,
        }
    },
    created() {
        console.log(this.isLightMode ? 'light mode' : 'dark mode');
    },
    methods: {
        toggleMode() {
            this.isLightMode = !this.isLightMode;
            this.path = this.isLightMode ? mdiWeatherNight : mdiWhiteBalanceSunny;
            document.querySelector('body').classList.contains('light') ? document.querySelector('body').classList.remove('light') : document.querySelector('body').classList.add('light');
            console.log(this.isLightMode ? 'light mode' : 'dark mode');
        },
        onKeyUp() {
            if (this.searchTimer) {
                clearTimeout(this.searchTimer);
            }
            this.searchTimer = setTimeout(() => {
                this.$emit('search', this.query);
            }, 1000);
        },
    }
}
</script>

<style lang="scss">
@import "../styles/_variables.scss";

.navbar {
    padding: 0 20px;
    .top {
        color: $white;
        display: flex;
        justify-content: space-between;
        align-items: center;
        /* height: 30px; */

        .right {
            display: flex;
            align-items: center;
            gap: 12px;
    
            svg:hover {
                cursor: pointer;
            }
            .menu {
                .menu-list {
                    display: none;
                }
            }
        }
    }


    ::placeholder {
        color: $med-gray;
        opacity: 1; /* Firefox */
    }
    .search {
            border-radius: 20px;
            border: none;
            padding: 12px 16px;
            background-color: $gray;
            color: $white;
            outline: none;
            width: 80%;
            max-width: 700px;
            box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
        }
}
</style>
