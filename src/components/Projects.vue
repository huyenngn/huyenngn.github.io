<template>
    <Filter @filter-projects="updateFilterList" :technologies="getTechnologies()" />
    <transition name="fade" tag="div">
        <div v-if="toggle">
            <Item v-for="(project, index) in filteredProjects" :key="index" :project="project"></Item>
        </div>
        <div v-else>
            <Item v-for="(project, index) in filteredProjects" :key="index" :project="project"></Item>
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
            if (this.filterList.length === 0) {
                return this.projects;
            }
            return this.projects.filter((project) =>
                this.filterList.some(tech => project.technologies.includes(tech))
            );
        },
    },
    data() {
        return {
            toggle: true,
            filterList: [],
            projects: [
                {
                    title: "✨ First and only Ô Ăn Quan AI",
                    text: "A Vietnamese traditional board game, Ô Ăn Quan, with an AI that uses the Minimax algorithm with Alpha-Beta pruning and Reinforcement Learning to play against human players. CI/CD to Google Compute Engine with GitHub Actions.This was part of my Bachelor's Thesis at TU Berlin.",
                    links: ["https://github.com/huyenngn/OAnQuan-AI", "http://35.239.5.44/"],
                    technologies: ["Python", "PyTorch", "OpenAI Gym", "Stable Baselines", "FastAPI", "Javascript", "Vue.js", "HTML", "CSS", "Docker", "GCP", "GitHub Actions", "CI/CD"],
                },
                {
                    title: "💻 LinuxTyper",
                    text: "A GUI auto-typer application for Linux that repeatedly executes keystrokes in a given time interval to any window - even minimised ones!",
                    links: ["https://github.com/huyenngn/linuxtyper"],
                    technologies: ["C", "CMake", "GTK", "Bash"],
                },
                {
                    title: "🚗 Autonomous LEGO Car",
                    text: "A self-driving LEGO car that utilises Computer Vision to recognise road lanes and predict the direction in which the road is turning. This was part of a Software Engineering Project course at TU Berlin.",
                    links: ["https://www.tu.berlin/sese/studium-lehre/studierendenprojeke\#c719986"],
                    technologies: ["C", "C++", "CMake", "OpenCV", "Raspberry Pi", "Bluetooth"],
                },
                {
                    title: "🤖 Twitter Bot",
                    text: "A Python script that automatically replies to my favourite Thai actor’s tweets with their English translations using the Twitter API. Implemented text and image translation with Google's Vision API and Cloud Translation API, hosted with AWS.",
                    links: ["https://github.com/huyenngn/TwitterBot"],
                    technologies: ["Python", "Javascript", "Docker", "REST API", "GCP", "AWS"],
                },
                {
                    title: "📊 Real-time CSI Visualization Tool for ESP32",
                    text: "A tool that senses how wireless signals travel through their surroundings and visualises them in real-time on an ESP32. This was part of a Networks Project course at TU Berlin.",
                    links: ["https://github.com/huyenngn/CSI-Visualization-on-ESP32"],
                    technologies: ["C", "C++", "CMake", "FreeRTOS", "LVGL"],
                },
                {
                    title: "🎀 Ribbon Studio",
                    text: "A web-based document editor, specialised for florists to design funeral ribbons. Initially I made it with Bootstrap, then I rewrote it with Vanilla CSS and Javascript.",
                    links: ["https://github.com/huyenngn/Ribbon-Studio", "https://tranquil-taffy-c57164.netlify.app/"],
                    technologies: ["Javascript", "Vue.js", "HTML", "CSS"],
                },
                {
                    title: "🌐 Portfolio Website",
                    text: "This Website.",
                    links: ["https://github.com/huyenngn/huyenngn.github.io", "https://huyenngn.github.io/"],
                    technologies: ["Javascript", "Vue.js", "HTML", "CSS"],
                },
            ],
        };
    },
};
</script>

<style>
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