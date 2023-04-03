
<template >
    <nav class="navbar">
        <h3>{{title}}</h3>
        <div class="right">
            <template v-if="isLightMode">
                <DarkIcon type="mdi" :path="path" title="dark mode" fillColor="#eeeeee" size="24" @click="toggleMode" />
            </template>
            <template v-else>
                <LightIcon type="mdi" :path="path" title="light mode" fillColor="#eeeeee" size="24" @click="toggleMode" />
            </template>
            <input class="search" type="text" name="search" id="search" placeholder="Search">
            <div class="menu">
                <MenuIcon title="menu" size="30" @click="toggleMode" />
                <div class="menu-list">
                    <p>Login</p>
                </div>
            </div>
        </div>
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
            title: 'Vue Counter',
            path: this.isLightMode ? mdiWeatherNight : mdiWhiteBalanceSunny,
            isLightMode: false,
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
        }
    }
}
</script>

<style lang="scss">
@import "../styles/_variables.scss";

.navbar {
  color: $white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  /* height: 30px; */
  padding: 0 20px;

    .right {
        display: flex;
        align-items: center;
        gap: 12px;

        .search {
            border-radius: 20px;
            border: none;
            padding: 12px 16px;
            background-color: $white;
            color: $black;
            outline: none;
        }

        svg:hover {
            cursor: pointer;
        }

        .menu {
            
            .menu-list {
                display: none;
            }
        }
    }

    ::placeholder {
        color: $black;
        opacity: 1; /* Firefox */
    }
}
</style>