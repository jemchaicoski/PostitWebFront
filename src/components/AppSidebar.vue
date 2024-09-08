<template>
    <aside :class="`${isExpanded ? 'is-expanded' : 'is-collapsed'}`">
        <div class="logo">
            <img src="../assets/logo.svg" alt="logo" />
        </div>

        <div class="menu-toggle-wrap">
            <button class="menu-toggle" @click="ToggleAppSideBar">
                <span class="material-symbols-outlined"> double_arrow </span>
            </button>
        </div>

        <div class="menu">
            <router-link class="button" to="/">
                <span class="material-symbols-outlined">sticky_note</span>
                <h1 class="text">Board</h1>
            </router-link>

            <router-link class="button" to="/about">
                <span class="material-symbols-outlined">question_mark</span>
                <h1 class="text">About</h1>
            </router-link>
        </div>
    </aside>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isExpanded = ref(false)

const ToggleAppSideBar = () => {
    isExpanded.value = !isExpanded.value
    localStorage.setItem('sidebarState', JSON.stringify(isExpanded.value));
}

onMounted(() => {
    const savedState = localStorage.getItem('sidebarState');
    if (savedState !== null) {
        isExpanded.value = JSON.parse(savedState);
    }
});
</script>

<style lang="scss" scoped>
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
        margin-left: 2.5rem;

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
            top: -4rem;
            left: 0.5rem;

            .menu-toggle {
                transform: rotate(-180deg);
            }
        }

        .menu {
            .button {
                display: flex;
                align-items: center;
                min-width: 100%;

                .material-icons {
                    margin-right: 1rem;
                }

                .text {
                    opacity: 1;
                    visibility: visible;
                    position: inline;
                    padding-left: 1rem;
                }
            }
        }

        .footer {
            opacity: 0;
        }
    }

    &.is-collapsed {
        .menu {
            .text {
                opacity: 0;
                visibility: hidden;
                position: absolute;
                transition: opacity 0.5s ease, visibility 0.5s ease;
            }
        }
    }

    .menu {
        display: flex;
        flex-direction: column;
        align-items: flex-start;

        .material-symbols-outlined {
            font-size: 30px;
        }

        .button {
            .text {
                opacity: 0;
                transition: opacity 0.2s ease 0.2s, display 0.2s ease 0.2s;
            }
        }
    }
}
</style>
