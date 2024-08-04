<template>
  <div class="main-wrapper">
    <main>
      <router-view v-slot="{ Component }">
        <template v-if="Component">
          <KeepAlive>
            <Suspense>
              <!-- main content -->
              <component :is="Component"></component>

              <!-- loading state -->
              <template #fallback>
                <div>Loading...</div>
              </template>
            </Suspense>
          </KeepAlive>
        </template>
        <template v-else>
          <div>Loading..........</div>
        </template>
      </router-view>
    </main>
    <Drawer />
  </div>
</template>

<script setup>
import Drawer from './components/Drawer.vue';

// enable primevue ripple effect
import { onMounted } from 'vue';
import PrimeVue from 'primevue/config';

onMounted(() => {
  PrimeVue.ripple = true;
});
</script>

<style lang="scss">
@import "./assets/scss/fonts";
@import "./assets/scss/index";


:root {
  font-size: max(16px, 0.73vw);
}

@media screen and (max-width: 1024px) {
  :root {
    font-size: 16px;
  }
}

@media screen and (max-width: 768px) {
  :root {
    font-size: 14px;
  }
}

@media screen and (max-width: 600px) {
  :root {
    font-size: 14px;
  }
}

html {
  font-family: "Roboto", cursive;
  height: 100%;
}
body {
  height: 100%;
}

#app {
  height: 100%;
}

</style>
<style lang="scss" scoped>
.main-wrapper {
  display: flex;
  justify-content: space-between;
  height: 100%;
  width: 100%;

  main {
    width: 100%;
  }
}
</style>