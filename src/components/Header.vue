<script setup lang="ts">
import type { Page } from '../interfaces/index';


    defineProps<{
        page: Page
    }>()

    const emit = defineEmits<{
        (e: 'navigate', page: Page): void
    }>()

</script>

<template>
    <header class="px-20 d-flex flex-row align-items-center">
        <a href="/" class="d-flex align-items-center mr-20">
            <img src="../assets/halloween-pirates-skeleton-svgrepo-com.svg" alt="logo">
            <span class="logo">Dyma</span>
        </a>
        <ul class="d-flex flex-row flex-fill">
            <li class="mr-10">
                <a :class="{ active: page === 'Boutique' }" @click="emit('navigate', 'Boutique')">Boutique</a>
            </li>
            <li>
                <a :class="{ active: page === 'Admin' }" @click="emit('navigate', 'Admin')">Admin</a>
            </li>
        </ul>
        <ul class="d-flex flex-row">
            <li class="mr-10">
                <a href="/">Inscription</a>
            </li>
            <li>
                <a href="/">Connexion</a>
            </li>
        </ul>
    </header>
</template>

<style scoped lang="scss">
    header {
        background-color: var(--primary-1);
        a {
            color: var(--text-primary-color);
            img {
                width: 20px;
                margin-right: 5px;
            }

            .logo {
                font-weight: 700;
                font-size: 20px;
            }
        }
        a.active {
            text-decoration: underline;
        }

        ul {
            display: flex;
        }
    }
</style>