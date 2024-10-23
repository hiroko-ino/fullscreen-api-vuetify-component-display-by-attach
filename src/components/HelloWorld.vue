<template>
  <v-container class="fill-height">
    <v-responsive
      class="align-centerfill-height mx-auto"
      max-width="900"
    >
      <v-card color="blue-darken-2" height="600" ref="el">
        <v-card-title>
          <h1>Fullscreen API Area</h1>
        </v-card-title>
        <v-card-text>
          <p>
            this is a fullscreen API area.
          </p>
        </v-card-text>
        <div class="d-flex ga-4 px-4">
          <v-menu
            open-on-hover
            :attach="true"
          >
            <template v-slot:activator="{ props }">
              <v-btn
                color="primary"
                v-bind="props"
              >
                Dropdown can display fullscreen
              </v-btn>
            </template>

            <v-list>
              <v-list-item
                v-for="(item, index) in items"
                :key="index"
              >
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
          <v-menu
            open-on-hover
          >
            <template v-slot:activator="{ props }">
              <v-btn
                color="primary"
                v-bind="props"
              >
                Dropdown can't display fullscreen
              </v-btn>
            </template>

            <v-list>
              <v-list-item
                v-for="(item, index) in items"
                :key="index"
              >
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </div>
        <div class="mt-8 px-4">
          <v-btn @click="toggle">toggle fullscreen</v-btn>
        </div>
      </v-card>
    </v-responsive>
  </v-container>
</template>

<script setup lang="ts">
import { useFullscreen } from '@vueuse/core';
import { ref } from 'vue';

const el = ref<HTMLElement | null>(null)

const { toggle } = useFullscreen(el)

  const items = [
    { title: 'Item 1' },
    { title: 'Item 2' },
    { title: 'Item 3' },
    { title: 'Item 4' },
  ];
</script>
