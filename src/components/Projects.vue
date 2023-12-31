<template>
    <Filter @filter-projects="updateFilterList" :technologies="getTechnologies()" />
    <transition name="fade" tag="div">
        <div v-if="toggle">
            <Item v-for="(project, index) in filteredProjects" :key="index" :project="project"
                class="card"></Item>
        </div>
        <div v-else>
            <Item v-for="(project, index) in filteredProjects" :key="index" :project="project"
                class="card"></Item>
        </div>
    </transition>
</template>

<script>
import Filter from './ProjectsFilter.vue'
import Item from './ProjectsItem.vue'

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
                    text: "A self-driving LEGO car that recognises road lanes and predicts the direction in which the car is turning.",
                    github: "",
                    git: "https://git.tu-berlin.de/sees-driving-1/raspberrypi",
                    link: "https://www.tu.berlin/sese/studium-lehre/studierendenprojeke\#c719986",
                    technologies: ["C", "C++", "CMake", "OpenCV"],
                },
                {
                    title: "📊 Real-time CSI Visualization Tool for ESP32",
                    text: "A tool that senses and visualises how wireless signals travel through their surroundings in real-time.",
                    github: "https://github.com/huyenngn/CSI-Visualization-on-ESP32",
                    git: "",
                    link: "",
                    technologies: ["C", "C++", "CMake", "FreeRTOS", "LVGL"],
                },
                {
                    title: "🍽️ Smart Kitchen",
                    text: "Bachelor Project Ambient Assisted Living",
                    github: "https://github.com/huyenngn/fridgeGPT",
                    git: "",
                    link: "",
                    technologies: ["Python", "FastAPI", "Express.js", "SQLite", "Prisma", "Typescript", "Docker Compose"],
                },
                {
                    title: "💻 LinuxTyper",
                    text: "An auto-typer for Linux that repeatedly executes keystrokes in any specified minimised or maximised window.",
                    github: "https://github.com/huyenngn/linuxtyper",
                    git: "",
                    link: "",
                    technologies: ["C", "CMake", "GTK"],
                },
                {
                    title: "🤖 Twitter Bot",
                    text: "A Python script that automatically replies to my favourite Thai actor’s tweets with their English translations.",
                    github: "https://github.com/huyenngn/TwitterBot",
                    git: "",
                    link: "",
                    technologies: ["Python", "Javascript", "Google Cloud", "Docker", "AWS"],
                },
                {
                    title: "🎀 Ribbon Designer",
                    text: "A web-based text editor, created for florists to design funeral ribbons.",
                    github: "https://github.com/huyenngn/RibbonDesigner",
                    git: "",
                    link: "https://tranquil-taffy-c57164.netlify.app/",
                    technologies: ["Javascript", "Vue.js", "Bootstrap", "HTML", "CSS"],
                },
                {
                    title: "🌐 Dynamic Portfolio Website",
                    text: "This Website.",
                    github: "https://github.com/huyenngn/resume",
                    git: "",
                    link: "https://resume-huyenngn.vercel.app/",
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