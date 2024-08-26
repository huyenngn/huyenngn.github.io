<script setup>
import Experience from './Experience.vue';
import InfoItem from './InfoItem.vue';
import Projects from './Projects.vue';
import CommunityIcon from './icons/IconCommunity.vue';
import DocumentationIcon from './icons/IconDocumentation.vue';
import SupportIcon from './icons/IconSupport.vue';
import ToolingIcon from './icons/IconTooling.vue';
</script>

<template>
    <InfoItem id="education">
        <template #icon>
            <DocumentationIcon />
        </template>
        <template #heading>Education</template>
        <ul>
            <li>
                Student at TUB (🇩🇪 Technical University of Berlin), 10/2018
                entry,
                <span class="bold">BSc in CE</span>
                .
            </li>
            <li>
                <span class="bold">Fields of Interest:</span>
                Embedded Systems and Software Development.
            </li>
        </ul>
    </InfoItem>

    <InfoItem id="work">
        <template #icon>
            <ToolingIcon />
        </template>
        <template #heading>Work Experience</template>
        <Experience />
    </InfoItem>

    <InfoItem id="projects">
        <template #icon>
            <SupportIcon />
        </template>
        <template #heading>Personal Projects</template>
        <Projects />
    </InfoItem>

    <InfoItem id="contact">
        <template #icon>
            <CommunityIcon />
        </template>
        <template #heading>Contact</template>
        <li>
            <span class="bold">E-mail: </span>
            <a href="mailto:nganhuyennguyenthi@gmail.com">nganhuyennguyenthi@gmail.com</a>
        </li>
    </InfoItem>
</template>
