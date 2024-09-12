<script setup>
import Item from './ProjectsItem.vue';


const jobs = [
    {
        title: "🚄 Python Developer Working Student @ DB InfraGo",
        text: "Worked both part-time and full-time, starting in 09/2023. Maintained and contributed to the System Engineering Toolchain at DB InfraGo. Tool development lead of several internal and open-source projects.",
        links: ["https://github.com/DSD-DBS/py-capellambse", "https://github.com/DSD-DBS/capellambse-context-diagrams", "https://github.com/DSD-DBS/capella-ros-tools"],
        technologies: ["Python", "Capella", "React", "FastAPI", "TailwindCSS", "Docker", "CI/CD", "Github Actions"],
    },
];
</script>

<template>
    <div>
        <Item v-for="(job, index) in jobs" :key="index" :project="job"></Item>
    </div>
</template>
