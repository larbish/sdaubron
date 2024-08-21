<template>
  <UFooter>
    <template #left>
      <p class="text-gray-500 dark:text-gray-400 text-sm">
        Copyright © {{ new Date().getFullYear() }}. All rights reserved.
      </p>
      <UColorModeButton size="sm" />
    </template>

    <template #right>
      <UButton
        to="https://www.google.fr/maps/place/1+Rue+des+M%C3%A9sanges,+91400+Orsay/@48.6967101,2.1864111,17z/data=!3m1!4b1!4m6!3m5!1s0x47e5d61d09ae28b1:0x7a9c7ec2169b773f!8m2!3d48.6967066!4d2.188986!16s%2Fg%2F11smz8lpp5?entry=ttu"
        target="_blank"
        icon="i-heroicons-home"
        color="gray"
        variant="ghost"
      >
        <span class="hidden sm:block">1 rue des mésanges, 91400, Orsay</span>
      </UButton>
      <UButton
        to="tel:0169280765"
        target="_blank"
        icon="i-heroicons-phone"
        color="gray"
        variant="ghost"
      >
        <span class="hidden sm:block">01 69 28 07 65</span>
      </UButton>
      <UButton
        to="mailto:sandrine.daubron@wanadoo.fr"
        target="_blank"
        icon="i-heroicons-at-symbol-20-solid"
        color="gray"
        variant="ghost"
      >
        <span class="hidden sm:block">
          sandrine.daubron@wanadoo.fr
        </span>
      </UButton>
    </template>
  </UFooter>
</template>
