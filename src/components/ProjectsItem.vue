<template>
    <div>
        <h4>{{ project.title }}</h4>
        <div>{{ project.text }}</div>
        <div class="technologies">
            <div class="technology" v-for="tech in project.technologies" :innerHTML="tech">
            </div>
        </div>
        <div class="technologies">
            <a :href="link" v-for="link in project.links">
                <div class="icon">
                    <IconGithub v-if="link.startsWith('https://github.com')" />
                    <IconLink v-else />
                </div>
            </a>
        </div>

    </div>

</template>

<script>
import IconGit from './icons/IconGit.vue';
import IconGithub from './icons/IconGithub.vue';
import IconLink from './icons/IconLink.vue';

export default {
    name: "ProjectsItem",
    props: {
        project: {
            type: Object,
            required: true
        }
    },
    components: { IconGithub, IconGit, IconLink }
};
</script>

<style scoped>
.technologies {
    display: flex;
    flex-wrap: wrap;
    margin: 1em auto;
}

h4 {
    font-size: 1em;
    font-weight: 500;
    margin-bottom: 0.4rem;
    /* color: var(--color-heading); */
}

.icon {
    width: 1rem;
    height: 1rem;
    margin-right: 1em;
    display: flex;
    place-items: center;
    place-content: center;
}

.technology {
    margin-right: 1rem;
    color: grey;
}

a {
    color: var(--color-text);
}

a:hover {
    background-color: var(--color-background);
}
</style>