<script setup>
import Item from './ProjectsItem.vue';


const jobs = [
    {
        title: "🚄 Python Developer Working Student @ DB InfraGo",
        text: "Worked part-time as a Python Developer, starting in 03/2024. Maintained and contributed to the System Engineering Toolchain at DB InfraGo. Tool development lead of several internal and open-source projects.  <ul><li>Document generation</li><li>SVG rendering</li><li>Capella model transformation</li><li>Context diagram generation</li><li>Algorithm development for context collection</li><li>Documentation, testing, and CI/CD</li>",
        links: ["https://github.com/DSD-DBS/py-capellambse", "https://github.com/DSD-DBS/capellambse-context-diagrams",],
        technologies: ["Python", "Capella MBSE", "React", "FastAPI", "TailwindCSS"],
    },
    {
        title: "🚄 Internship @ DB InfraGo",
        text: "Full-time internship, starting in 09/2023.",
        links: ["https://github.com/DSD-DBS/capella-ros-tools"],
        technologies: ["Python"],
    },
];
</script>

<template>
    <div>
        <Item v-for="(job, index) in jobs" :key="index" :project="job"></Item>
    </div>
</template>
