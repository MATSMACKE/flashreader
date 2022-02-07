<template>
    <div>
        <input @change="toggleTheme" id="checkbox" type="checkbox" class="switch-checkbox" />
        <label for="checkbox" class="switch-label">
            <div
                class="switch-toggle"
                :class="{ 'switch-toggle-checked': theme === 'dark-theme' }"
            ></div>
        </label>
        <label for="checkbox" class="darkmode-label">
            <p id="darkmode-text">Dark Mode</p>
        </label>
    </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

export default class App extends Vue {
    theme = 'light-theme'

    mounted() {
        const initUserTheme = this.getMediaPreference();
        this.setTheme(initUserTheme);
    }

    toggleTheme() {
        const activeTheme = localStorage.getItem("user-theme");
        if (activeTheme === "light-theme") {
            this.setTheme("dark-theme");
        } 
        else {
            this.setTheme("light-theme");
        }
        
    }

    setTheme(theme: string) {
        localStorage.setItem("user-theme", theme);
        this.theme = theme;
        document.documentElement.className = theme;
    }

    getMediaPreference() {
        const hasDarkPreference = window.matchMedia(
            "(prefers-color-scheme: dark)"
        ).matches;
        if (hasDarkPreference) {
            return "dark-theme";
        } 
        else {
            return "light-theme";
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.switch-checkbox {
    display: none;
}

.switch-label {
    align-items: center;
    background: var(--text-primary-color);
    border: calc(var(--element-size) * 0.025) solid var(--accent-color);
    border-radius: var(--element-size);
    cursor: pointer;
    display: flex;
    font-size: calc(var(--element-size) * 0.3);
    height: calc(var(--element-size) * 0.35);
    position: relative;
    padding: calc(var(--element-size) * 0.1);
    transition: background 0.5s ease;
    justify-content: space-between;
    width: var(--element-size);
    z-index: 1;
    transform: scale(0.5, 0.5) translate(20px, 20px);
}

.switch-toggle {
    position: absolute;
    background-color: var(--background-color-primary);
    border-radius: 50%;
    top: calc(var(--element-size) * 0.07);
    left: calc(var(--element-size) * 0.07);
    height: calc(var(--element-size) * 0.4);
    width: calc(var(--element-size) * 0.4);
    transform: translateX(0);
    transition: transform 0.3s ease, background-color 0.5s ease;
}

.switch-toggle-checked {
    transform: translateX(calc(var(--element-size) * 0.6)) !important;
}
.darkmode-label {
    align-items: center;
    display: flex;
    font-size: calc(var(--element-size) * 0.2);
    height: calc(var(--element-size) * 0.35);
    position: absolute;
    padding: calc(var(--element-size) * 0.1);
    transition: background 0.5s ease;
    justify-content: space-between;
    left: 20px;
    width: 150px;
    z-index: 1;
}
#darkmode-text {
    color: var(--text-primary-color);
}
</style>
