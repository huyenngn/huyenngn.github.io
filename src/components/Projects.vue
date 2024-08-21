<template>
    <Filter @filter-projects="updateFilterList" :technologies="getTechnologies()" />
    <transition name="fade" tag="div">
        <div v-if="toggle">
            <Item v-for="(project, index) in filteredProjects" :key="index" :project="project" class="card"></Item>
        </div>
        <div v-else>
            <Item v-for="(project, index) in filteredProjects" :key="index" :project="project" class="card"></Item>
        </div>
    </transition>
</template>

<script>
import Filter from './ProjectsFilter.vue';
import Item from './ProjectsItem.vue';

export default {
    name: "App",
    components: {
        Filter,
        Item,
    },
    methods: {
        getTechnologies() {
            let technologies = [];
            this.projects.forEach(project => {
                project.technologies.forEach(tech => {
                    if (!technologies.includes(tech)) {
                        technologies.push(tech)
                    }
                });
            });
            return technologies;
        },
        updateFilterList(filter) {
            this.filterList = filter;
            this.toggle = !this.toggle;
        },
    },
    computed: {
        filteredProjects() {
            return this.projects.filter((project) =>
                this.filterList.every(tech => project.technologies.includes(tech))
            );
        },
    },
    data() {
        return {
            toggle: true,
            filterList: [],
            projects: [
                {
                    title: "🚗 Autonomous LEGO Car",
                    text: "A self-driving LEGO car that utilises Computer Vision to recognise road lanes and predict the direction in which the road is turning. This was part of a Software Engineering Project course at TU Berlin.",
                    links: ["https://www.tu.berlin/sese/studium-lehre/studierendenprojeke\#c719986"],
                    technologies: ["C", "C++", "CMake", "OpenCV"],
                },
                {
                    title: "💻 LinuxTyper",
                    text: "A GUI auto-typer application for Linux that repeatedly executes keystrokes in a given time interval to any window - even minimised ones!",
                    links: ["https://github.com/huyenngn/linuxtyper"],
                    technologies: ["C", "CMake", "GTK"],
                },
                {
                    title: "🤖 Twitter Bot",
                    text: "A Python script that automatically replies to my favourite Thai actor’s tweets with their English translations using Google Cloud Services, hosted with AWS. It also translates text in images!",
                    links: ["https://github.com/huyenngn/TwitterBot"],
                    technologies: ["Python", "Javascript", "Google Cloud", "Docker", "AWS"],
                },
                {
                    title: "📊 Real-time CSI Visualization Tool for ESP32",
                    text: "A tool that senses how wireless signals travel through their surroundings and visualises them in real-time on an ESP32. This was part of a Networks Project course at TU Berlin.",
                    links: ["https://github.com/huyenngn/CSI-Visualization-on-ESP32"],
                    technologies: ["C", "C++", "CMake", "FreeRTOS", "LVGL"],
                },
                {
                    title: "🎀 Ribbon Designer",
                    text: "A web-based document editor, specialised for florists to design funeral ribbons. Initially I made it with Bootstrap, then I rewrote it with Vanilla CSS and Javascript.",
                    links: ["https://github.com/huyenngn/RibbonDesigner", "https://tranquil-taffy-c57164.netlify.app/"],
                    technologies: ["Javascript", "Vue.js", "HTML", "CSS"],
                },
                {
                    title: "🌐 Portfolio Website",
                    text: "This Website.",
                    links: ["https://github.com/huyenngn/resume", "https://huyenngn.github.io/"],
                    technologies: ["Javascript", "Vue.js", "HTML", "CSS"],
                },
            ],
        };
    },
};
</script>

<style>
.card {
    min-width: 0;
    padding-bottom: 5px;
    margin-bottom: 5px;
    border-bottom: 1px solid var(--color-border);
}

.card:last-of-type {
    border-bottom: 0;
}

.fade-enter-active {
    animation: fade .5s;
}

.fade-leave-active {
    animation: fade .5s reverse;
}


@keyframes fade {
    0% {
        opacity: 0;
    }

    50% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}
</style>