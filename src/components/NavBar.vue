<template>
    <nav role='navigation'>
        <ul>
            <li v-for="link in links">
                <a :href="'#' + link.id" @click="scrollIntoView($event, link.id)">{{ link.text }}</a>
            </li>
            <li>
                <ThemeSwitch @toggleTheme="toggleTheme()" :theme="this.theme" />
            </li>
        </ul>

    </nav>
</template>

<script>
import ThemeSwitch from './ThemeSwitch.vue';
import IconCross from './icons/IconCross.vue';
import IconMoon from './icons/IconMoon.vue';
import IconSun from './icons/IconSun.vue';
import IconTheme from './icons/IconTheme.vue';

export default {
    name: "NavBar",
    props: {
        links: {
            type: Object,
            required: true
        },
    },
    data() {
        return {
            theme: "",
        };
    },
    mounted() {
        let localTheme = localStorage.getItem("theme");
        if (localTheme == "darkMode" || localTheme == "lightMode") {
            this.theme = localTheme;
        }
        else if (window.matchMedia && screen && window.matchMedia("(prefers-color-scheme: dark)").matches) {
            this.theme = "darkMode";
        }
        else {
            this.theme = "lightMode";
        }
        document.documentElement.setAttribute("data-theme", this.theme);
    },
    methods: {
        toggleTheme() {
            this.theme = this.theme == "darkMode" ? "lightMode" : "darkMode";
            document.documentElement.setAttribute("data-theme", this.theme);
            localStorage.setItem("theme", this.theme);
        },
        scrollIntoView(e, id) {
            e.preventDefault();
            console.log(id);
            document.getElementById(id).scrollIntoView({ behavior: "smooth" });
        }
    },
    components: { IconMoon, IconSun, IconTheme, ThemeSwitch, IconCross }
};
</script>

<style scoped>
.userActive {
    background-color: hsla(160, 100%, 37%, 1);
    ;
}

nav {
    display: none;
}



nav ul {
    list-style: none;
    display: flex;
    gap: 1rem;
    align-items: center;
}

nav ul li:last-of-type {
    border-left: 1px solid var(--color-border);
}

.invisible {
    display: none;
}

#modal {
    background-color: var(--color-background);
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    z-index: 1;
    padding: 2rem;
}

#modal div {
    display: flex;
    padding-bottom: 1rem;
    align-items: center;
}

.closebtn {
    justify-content: end;
}

.closebtn>* {
    width: 20px;
    height: 20px;
    cursor: pointer;
}

@media (min-width: 1024px) {
    nav {
        display: flex;
        justify-content: flex-end;
        position: relative;
        top: 0;
        right: 0;
        padding: 1rem 1rem;
        font-size: 1.125rem;
    }
}

@media print {
    nav {
        display: none;
    }

}
</style>