<template>
    <div>
        <input @change="toggleTheme" id="checkbox" type="checkbox" class="switch-checkbox" />
        <label for="checkbox" class="switch-label">
            <div
                class="switch-toggle"
                :class="{ 'switch-toggle-checked': theme === 'dark' }"
            ></div>
        </label>
        <label for="checkbox" class="darkmode-label">
            <p id="darkmode-text">Dark Mode</p>
        </label>
    </div>
</template>

<script lang="ts">
import { Vue } from 'vue-class-component';

export default class App extends Vue {
    theme = 'light'

    mounted(): void {
        const initUserTheme = this.getPreferred();
        this.setTheme(initUserTheme);
    }

    toggleTheme(): void {
        const activeTheme = localStorage.getItem("theme");
        this.setTheme(activeTheme === "light" ? "light" : "dark")
        if (activeTheme === "light") {
            this.setTheme("dark");
        }
        else {
            this.setTheme("light");
        }
        
    }

    setTheme(theme: string): void {
        localStorage.setItem("theme", theme);
        this.theme = theme;
        document.documentElement.className = theme;
    }

    getPreferred(): string {
        const hasDarkPreference = window.matchMedia(
            "(prefers-color-scheme: dark)"
        ).matches;
        if (hasDarkPreference) {
            return "dark";
        } 
        else {
            return "light";
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
    transition: background var(--transition-time) ease;
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
    transition: transform 0.3s ease, background-color var(--transition-time) ease;
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
    transition: background var(--transition-time) ease;
    justify-content: space-between;
    left: 20px;
    width: 150px;
    z-index: 1;
}
#darkmode-text {
    color: var(--text-primary-color);
}
</style>
