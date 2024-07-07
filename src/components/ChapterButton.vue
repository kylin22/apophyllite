<script setup lang="ts">
    import { ref } from "vue";
    import { Chapter } from "../book/bookType";
    const props = defineProps<{
        chapter: Chapter
    }>()

    const expanded = ref(false);
</script>

<template>
    <li>
        <b><a @mouseup="expanded = !expanded" id="chapter">{{ chapter.title }}</a></b>
        <TransitionGroup name="expand" mode="out-in">
            <ul v-if="expanded">
                <li v-for="subchapter in chapter.subChapters" :key="subchapter.title">
                    <RouterLink id="subchapter" to="#" >{{ subchapter.title }}</RouterLink>
                </li>
            </ul>
        </TransitionGroup>
    </li>
</template>

<style scoped lang="scss">
    ul {
        list-style-type: none;
        padding-left: 0px;
        margin: 10px;
    }

    #chapter, #subchapter {
        display: inline-flex;
        justify-content: center;
        width: 500px;
        transition: letter-spacing 0.5s;
        text-decoration: none;
        color: inherit;
        cursor: pointer;

        &:hover, &:focus {
            outline-offset: 0px;
            letter-spacing: 6px;
            outline: 2px solid white;
        }

        &:active {
            background-color: #fff;
        }
    }
    
    .expand-enter-active,
    .expand-leave-active {
        transition: opacity, line-height, padding, color, margin, 0.4s;
    }

    .expand-enter-from,
    .expand-leave-to {
        opacity: 0;
        line-height: 0;
        padding: 0 1em;
        color: transparent;
        margin: 0px;
    }
    
</style>
