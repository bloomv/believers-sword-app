<template>
    <div id="right-side-bar" class="h-[100%] w-[100%] select-none dark:bg-black dark:bg-opacity-20 bg-gray-200">
        <RightSideMenuBar />
        <div class="h-[100%] w-[100%]">
            <SearchTab v-show="tabValue === 'searchTab'" />
            <SelectBibleVersions v-if="tabValue === 'versionsTab'" />
            <Bookmarks v-if="tabValue === 'bookmarksTab'" />
            <MarkedHighlights v-if="tabValue === 'MarkedHighlights'" />
            <ShowClipNotes v-show="tabValue === 'MyNotes'" />
        </div>
    </div>
</template>
<script lang="ts">
import { computed, defineComponent } from "vue";
import SelectBibleVersions from "./SelectBibleVersions/SelectBibleVersions.vue";
import SearchTab from "./Search/Search.vue";
import Bookmarks from "./Bookmarks/Bookmarks.vue";
import { useStore } from "vuex";
import RightSideMenuBar from "@/components/ReadBiblePageComponents/RightSide/rightSideMenuBar/rightSideMenuBar.vue";
import MarkedHighlights from "./MarkedHighlights/MarkedHighlights.vue";
import ShowClipNotes from "./showClipNotes/showClipNotes.vue"

export default defineComponent({
    name: "ReadBibleChapterRightSide",
    components: { SelectBibleVersions, Bookmarks, SearchTab, RightSideMenuBar, MarkedHighlights, ShowClipNotes },
    setup() {
        const store = useStore();
        const tabValue = computed(() => store.state.rightMenuTab);
        return {
            tabValue
        };
    }
});
</script>
<style lang="postcss">
#right-side-bar {
    --right-side-tab-height: 40px;
}
</style>
