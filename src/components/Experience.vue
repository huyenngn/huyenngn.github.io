<script setup>
import Item from './ProjectsItem.vue';


const jobs = [
    {
        title: "🚄 Software Developer @ DB InfraGo",
        text: "<ul><li>Full-time internship, starting in 09/2023, and subsequent part-time work as a Software Development Working Student since 03/2024</li><li>Maintained and contributed to the System Engineering Toolchain at DB InfraGo that aid 'AutomatedTrain' and other DBS projects</li><li>Shipped the Cable Tree View for the py-capellambse 'Context Diagrams' extension among other features</li><li>Tool development lead of Capella ROS Tools</li><li>Frontend developement lead of Polarion Config Diff Tool</li><li>Contributed to py-capellambse e.g. 'sync' operation of the 'decl' module</li><li>Documentation, testing, and CI/CD with Github Actions</li>",
        links: ["https://github.com/DSD-DBS/py-capellambse", "https://github.com/DSD-DBS/capellambse-context-diagrams",],
        technologies: ["Python", "Vue.js", "React", "FastAPI", "TailwindCSS", "GitHub Actions",],
    },
];
</script>

<template>
    <div>
        <Item v-for="(job, index) in jobs" :key="index" :project="job"></Item>
    </div>
</template>
