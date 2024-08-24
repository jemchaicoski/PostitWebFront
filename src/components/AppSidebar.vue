<template>
    <aside :class="`${isExpanded && 'is-expanded'}`">
        <div class="logo">
            <img src="../assets/logo.svg" alt="logo">
        </div>

        <div class="menu-toggle-wrap">
            <button class="menu-toggle" @click="ToggleMenu">
                <span class="material-symbols-outlined">
                    double_arrow
                </span>
            </button>
        </div>

        <h3>Menu</h3>
        <div class="menu">
            <router-link class="button" to="/">
                <span class="material-symbols-outlined">sticky_note</span>
                <span class="text">Board</span>
            </router-link>

            <router-link class="button" to="/about">
                <span class="material-symbols-outlined">question_mark</span>
                <span class="text">About</span>
            </router-link>
        </div>
    </aside>
</template>

<script setup>
import { ref } from 'vue';

const isExpanded = ref(false);

const ToggleMenu = () => {
    isExpanded.value = !isExpanded.value;
}
</script>

<style Lang="sass" scoped>
aside {
    display: flex;
    flex-direction: column;

    background-color: var(--vt-c-black-soft);
    color: var(--vt-c-white-soft);

    width: calc(2rem + 2rem);
    min-height: 100vh;
    overflow: hidden;
    padding: 1rem;

    transition: 0.2s ease-out;

    .flex {
        flex: 1 1 0%;
    }

    .logo {
        margin-bottom: 1rem;

        img {
            width: 2rem;
        }
    }

    .menu-toggle-wrap {
        display: flex;
        justify-content: flex-end;
        margin-bottom: 1rem;

        position: relative;
        top: 0;
        transition: 0.2s ease-in-out;

        .menu-toggle {
            transition: 0.2s ease-in-out;

            .material-symbols-outlined {
                font-size: 2rem;
                color: var(--vt-c-white-soft);
                transition: 0.2s ease-out;
            }

            &:hover {
                .material-symbols-outlined {
                    color: var(--primary);
                    transform: translateX(0.5rem);
                }
            }
        }
    }

    &.is-expanded {
        width: var(--sidebar-width);

        .menu-toggle-wrap {
            top: -3rem;

            .menu-toggle {
                transform: rotate(-180deg);
            }
        }

        h3,
        .button .text {
            opacity: 1;
        }

        .button {
            .material-icons {
                margin-right: 1rem;
            }
        }

        .footer {
            opacity: 0;
        }
    }

    @media (max-width: 1024px) {
        position: absolute;
        z-index: 99;
    }
}
</style>