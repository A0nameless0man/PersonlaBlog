<template>
    <div id="app">
        <a-layout>
            <a-layout-header
                class="header"
                :style="{ position: 'fixed', zIndex: 1, width: '100%' }"
            >
                <a-menu
                    theme="dark"
                    mode="horizontal"
                    :selectable="false"
                >
                    <a-menu-item key="Home">
                        <router-link to="/">Home</router-link>
                    </a-menu-item>
                    <a-menu-item key="About">
                        <router-link to="/about">About</router-link>
                    </a-menu-item>
                    <a-menu-item key="ArticleList">
                        <router-link :to="'/article'">
                            <a-icon type="book" />
                            ArticleList
                        </router-link>
                    </a-menu-item>
                </a-menu>
            </a-layout-header>
            <a-layout-content :style="{ marginTop: '70px', padding: '0 10px' }">
                <div><router-view /></div>
            </a-layout-content>
            <a-layout-footer :style="{ textAlign: 'center' }">
                <p v-for="rec in records" v-bind:key="rec.href">
                    <a
                        :href="rec.href"
                        target="_blank"
                        rel="noopener noreferrer"
                    >
                        {{ rec.text }}
                    </a>
                </p>
            </a-layout-footer>
        </a-layout>
        <div style="padding: 3px" />
    </div>
</template>
<script>
import Vue from "vue";
import Component from "vue-class-component";
import { Button, Menu, Icon, Layout } from "ant-design-vue";
import { Article } from "@/util/Article";
import config from "@/config";
@Component({
    components: {
        AButton: Button,
        AMenu: Menu,
        AMenuItem: Menu.Item,
        ASubMenu: Menu.SubMenu,
        AIcon: Icon,
        ALayout: Layout,
        ALayoutHeader: Layout.Header,
        ALayoutContent: Layout.Content,
        ALayoutFooter: Layout.Footer,
        ALayoutSider: Layout.Sider
    }
})
class App extends Vue {
    records = config.other.records;
}

export default App;
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    height: 100%;
    display: flex;
    flex: 1 0 auto;
    text-align: center;
    color: #2c3e50;
}
html,
body {
    height: 100%;
}
</style>
