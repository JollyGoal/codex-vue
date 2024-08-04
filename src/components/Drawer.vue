<template>
    <Button class="open-drawer-btn" raised icon="fas fa-bars" aria-label="open drawer" severity="primary"  @click="openDrawer = true" />
    <div class="close-drawer-area" :class="{ open: openDrawer }" @click="openDrawer = false"
    ></div>
    <div class="main-container" :class="{ open: openDrawer }">
        <!-- <Divider layout="vertical" /> -->
        <div class="drawer">
            <div class="drawer-header">
                <h2>Codex<span style="color: var(--p-button-primary-background);">UZ</span></h2>
                <Button class="close-btn" icon="fas fa-times" aria-label="close drawer" @click="openDrawer = false" />
            </div>
            <Divider style="visibility: hidden;" />
            <Button raised icon="fas fa-plus" label="New chat" severity="primary" />
            <div class="section">
                <div class="section-header">
                    <div class="header-title">
                        <h5>Bookmarks</h5>
                    </div>
                    <Button outlined icon="fas fa-chevron-down" aria-label="Filter" severity="secondary" />
                </div>
                <div class="chat-links">
                    <router-link to="/" class="chat-router-link">Lorem ipsum </router-link>
                    <router-link to="/" class="chat-router-link">Lorem ipsum ipsum Lorem ipsum Lorem ipsum </router-link>
                    <router-link to="/" class="chat-router-link">rem ipsum Lorem ipsum Lorem ipsum Lorem ipsum </router-link>
                </div>
            </div>
            <div class="section">
                <div class="section-header">
                    <div class="header-title">
                        <h5>Recents</h5>
                    </div>
                    <Button outlined icon="fas fa-chevron-down" aria-label="Filter" severity="secondary" />
                </div>
                <div class="chat-links">
                    <router-link to="/" class="chat-router-link">Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum </router-link>
                    <router-link to="/" class="chat-router-link">Lorem ipsum </router-link>
                    <router-link to="/" class="chat-router-link">Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum </router-link>
                    <router-link to="/" class="chat-router-link">Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum </router-link>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import Divider from 'primevue/divider';
import Button from 'primevue/button';
import { ref } from 'vue';

const openDrawer = ref(false);

</script>

<style lang="scss" scoped>

.open-drawer-btn {
    display: none;
}

.close-drawer-area {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, 1);
    opacity: 0;
    z-index: 1000;
    cursor: pointer;
    pointer-events: none;
    transition: opacity 0.3s;
}

.main-container {
    position: relative;
    height: 100vh;
    max-height: 100vh;
    width: 26rem;
    display: flex;
    flex-direction: row;
    overflow: auto;
    border-left: 1px solid var(--p-divider-border-color);
    z-index: 1001;

    .drawer {
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        padding: 1rem;

        .drawer-header {
            height: 3rem;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: row;
            border-bottom: 1px solid var(--p-divider-border-color);
            margin-bottom: 1rem;

            .close-btn {
                display: none;
            }

            h2 {
                font-size: 1.5rem;
                font-weight: 500;
                margin: 0;
            }
        }

        .section {
            display: flex;
            flex-direction: column;
            margin-top: 1rem;

            .section-header {
                display: flex;
                justify-content: space-between;
                align-items: center;
                margin-bottom: 0.5rem;

                .header-title {
                    display: flex;
                    align-items: center;
                    color: var(--p-button-secondary-color);

                    h5 {
                        margin: 0;
                    }
                }
            }

            .chat-links {
                display: flex;
                flex-direction: column;

                .chat-router-link {
                    text-decoration: none;
                    text-wrap: nowrap;
                    overflow: hidden;
                    text-overflow: ellipsis;
                    color: var(--text-color);
                    padding: 0.6rem;
                    border-radius: 0.5rem;
                    margin-bottom: 0.5rem;
                    transition: background-color 0.3s;
                    background-color: var(--p-button-contrast-foreground);
                    color: var(--p-button-contrast-background);
                    font-weight: bold;

                    &:hover {
                        background-color: var(--p-button-contrast-background);
                        color: var(--p-button-contrast-color);
                    }
                }
            }
        }
    }
}

@media screen and (max-width: 768px) {
    .open-drawer-btn {
        display: block;
    }

    .close-drawer-area {
        pointer-events: none;
        opacity: 0;

        &.open {
            opacity: 0.5;
            pointer-events: all;
        }
    }

    .main-container {
        right: 0;
        position: fixed;
        width: 20rem;
        background-color: var(--p-content-background);
        transform: translateX(100%);
        transition: transform 0.3s;

        &.open {
            transform: translateX(0);
        }

        .drawer {

            .drawer-header {
                justify-content: space-between;

                .close-btn {
                    display: block;
                }
            }
        }
    }
}
</style>