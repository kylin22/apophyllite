<script setup lang="ts">
    import { onMounted, ref } from "vue";
    import part1 from "../book/book.json";
    import ChapterButton from "@/components/ChapterButton.vue";
    import { Part } from "../book/bookType";

    const bookData: Part = part1;
    const bgElement = ref<HTMLDivElement | null>(null);

    const grainImages = [
        "/grain/grain-01.png",
        "/grain/grain-02.png",
        "/grain/grain-03.png",
        "/grain/grain-04.png",
        "/grain/grain-05.png",
        "/grain/grain-06.png",
        "/grain/grain-07.png",
        "/grain/grain-08.png"
    ];

    let currentImageIndex = 0;
    onMounted(() => {
        const grainInterval = setInterval(() => {
            if (bgElement.value && grainImages.length > 0) {
                bgElement.value.style.backgroundImage = `url(${grainImages[currentImageIndex]})`;
                currentImageIndex = (currentImageIndex + 1) % grainImages.length;
            }
        }, 50);
    });
    
    
</script>

<template>
    <div id="vignette"></div>
    <div id="container" ref="bgElement" class="scanlines">
        <div id="title">
            <h1><i>{{ bookData.title }}</i></h1>
        </div>
        <nav id="chapters">
            <ul>
                <ChapterButton v-for="chapter in bookData.chapters" :chapter="chapter"/>
            </ul>
            
        </nav>
        <footer>
            <RouterLink id="more-info" to="#">//more_info//</RouterLink>
        </footer>
    </div>
    
</template>

<style scoped lang="scss">
    @use "../style/scanlines";

    footer {
        display: inline-flex;
        justify-content: center;
    }

    #more-info {
        font-size: small;
        transition: letter-spacing 0.5s;
        text-decoration: none;
        color: white;
        cursor: pointer;
        opacity: 0.5;
        transition: opacity 0.25s;
    }

    #more-info:hover {
        opacity: 1;
    }

    #container {
        pointer-events: auto;
        padding-bottom: 10px;
        height: 100%;
        overflow: hidden;
        display: flex;
        flex-direction: column;
        font-family: 'Times New Roman', Times, serif;
    }

    #title {
        margin-top: 50px;
        text-align: center;
        flex-grow: 0;
        text-decoration: underline
    }

    nav {
        margin-top: 20px;
        text-align: center;
        flex-grow: 1;
    }

    ul {
        list-style-type: none;
        padding-left: 0px;
        margin: 0px;
    }

    #vignette {
        pointer-events: none;
        z-index: 1;
        background: radial-gradient(circle, rgba(0,0,0,0) 25%, rgba(0,0,0,1) 100%);
        position: absolute;
        width: 100%;
        height: 100%;
    }
</style>