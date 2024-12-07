<template>
    <NavBar :links="links" />
    <main>
        <Header :fullName="fullName" />
        <Info />
    </main>
</template>

<script>
import Header from './components/Header.vue';
import Info from './components/Info.vue';
import NavBar from './components/NavBar.vue';

export default {
    name: "App",
    components: {
        Info,
        Header,
        NavBar
    },
    data() {
        return {
            fullName: "Huyen Nguyen",
            links: [
                {
                    text: "Education",
                    id: "education",
                },
                {
                    text: "Work",
                    id: "work",
                },
                {
                    text: "Projects",
                    id: "projects",
                },
                {
                    text: "Contact",
                    id: "contact",
                },
            ],
        }
    },
};
</script>

<style scoped>
main {
    margin: 0 auto;
    width: 100%;
    padding: 2.5rem 2rem;
}

@media (min-width: 1024px) {
    main {
        padding: 0;
        max-width: 700px;
    }
}

@media print {
    main {
        padding-top: 1rem;
    }
}
</style>