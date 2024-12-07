<script setup>
import Item from './ProjectsItem.vue';


const jobs = [
    {
        title: "🚄 Python Developer Working Student @ DB InfraGo",
        text: "<ul><li>Full-time internship, starting in 09/2023, and subsequent part-time work as a Software Development Working Student since 03/2024</li><li>Backend Development: Specializing in Python with a focus on developing tools for Model-Based Systems Engineering (MBSE) and Application Lifecycle Management (ALM).</li><li>Tool Ownership: Developing and maintaining multiple repositories, including Capella ROS Tools, and two internal Capella-related projects.</li><li>Documentation: Writing and maintaining documentation for developed code using Sphinx and MkDocs.</li><li>Open Source Contributions: Maintaining 7 repositories on GitHub, ensuring REUSE license compliance, QA, automated testing, and pre-commit hooks.</li>",
        links: ["https://github.com/DSD-DBS/capellambse-context-diagrams", "https://github.com/DSD-DBS/capella-ros-tools", "https://github.com/DSD-DBS/py-capellambse", "https://github.com/DSD-DBS/capella-model-explorer"],
        technologies: ["Python", "Vue.js", "React", "FastAPI", "TailwindCSS", "GitHub Actions", "Docker"],
    },
];
</script>

<template>
    <div>
        <Item v-for="(job, index) in jobs" :key="index" :project="job"></Item>
    </div>
</template>
