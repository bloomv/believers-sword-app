<template>
    <div>
        <div class="flex items-center gap-15px">
            <h1 class="font-700">Enable Dark Theme</h1>
            <div>
                <NSwitch v-model:value="isDarkTheme" @update:value="handleThemeChange" />
            </div>
        </div>
        <small>If this is on, the theme will change to dark theme if not it will light theme.</small>
    </div>
</template>
<script lang="ts">
import { defineComponent, onMounted, ref } from "vue";
import { NSwitch } from "naive-ui";
import { useStore } from "vuex";
import session from "@/service/session/session";
export default defineComponent({
    components: {
        NSwitch
    },
    setup() {
        const store = useStore();
        const isDarkTheme = ref(true);

        onMounted(() => {
            isDarkTheme.value = store.state.dark;
        });

        return {
            isDarkTheme,
            handleThemeChange(value: boolean) {
                store.state.dark = value;
                session.set("believers-sword-ui-theme", value ? "dark" : "light");
            }
        };
    }
});
</script>
