<script setup lang="ts">
import type { NavItem } from '@nuxt/content'

const navigation = inject<Ref<NavItem[]>>('navigation', ref([]))

const links = [{
  label: 'Prestations',
  to: '/prestations'
}, {
  label: 'Contact',
  to: '/contact'
}]
</script>

<template>
  <UHeader :links="links">
    <template #logo>
      Sandrine Daubron <UBadge
        label="Pédicure Podologue"
        variant="subtle"
        class="mb-0.5"
      />
    </template>

    <template #right>
      <UButton
        label="Prendre rendez-vous"
        icon="i-heroicons-arrow-right-20-solid"
        trailing
        color="black"
        to="https://www.doctolib.fr/pedicure-podologue/orsay/sandrine-daubron"
        target="_blank"
        class="hidden lg:flex"
      />
    </template>

    <template #panel>
      <UNavigationTree
        :links="mapContentNavigation(navigation)"
        default-open
      />
    </template>
  </UHeader>
</template>
