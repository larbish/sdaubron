<template>
  <UContainer>
    <UPage>
      <UPageBody>
        <UPageHero
          :title="page.hero.title"
          :description="page.hero.description"
          align="left"
          :links="page.hero.links"
        >
          <div class="flex justify-center items-center gap-4">
            <NuxtImg
              height="200"
              width="200"
              class="rounded-md shadow-xl ring-1 ring-gray-300 dark:ring-gray-700"
              src="sandrine_daubron.jpg"
            />
          </div>
        </UPageHero>

        <UPageGrid
          :ui="{ wrapper: 'xl:grid-cols-2' }"
          class="mb-20 sm:mb-24"
        >
          <UPageCard
            icon="i-heroicons-currency-euro"
            title="Remboursements"
          >
            <template #description>
              <p>
                Conventionné.
              </p>
              <p>
                Carte vitale non accepté.
              </p>
              <p>
                Tiers payant: Sécurité sociale.
              </p>
            </template>
          </UPageCard>
          <UPageCard
            icon="i-heroicons-credit-card"
            title="Moyens de paiement"
          >
            <template #description>
              <p class="text-red-500 font-medium">
                Cartes bancaires non acceptées
              </p>
              <p>
                Chèques et espèces
              </p>
            </template>
          </UPageCard>
        </UPageGrid>

        <ULandingCard
          title="Informations d'accès"
          icon="i-heroicons-map-pin"
          color="primary"
          orientation="horizontal"
          :ui="{ icon: { base: 'text-primary w-10 h-10' } }"
        >
          <template #description>
            <p class="py-3">
              1 rue des mésanges, 91400 Orsay
            </p>
            <p class="font-medium">
              Moyen de transport:
            </p>
            <p>
              RER B - Orsay Ville
              RER B - Le Guichet
            </p>
          </template>
          <NuxtImg
            width="600"
            height="300"
            src="contact_entry.JPG"
            class="w-full rounded-md"
          />
        </ULandingCard>
      </UPageBody>

      <UPageCard
        title="Formations"
        icon="i-heroicons-academic-cap"
        class="mb-20 sm:mb-24"
      >
        <UTable
          class="mt-5"
          :rows="studies"
          :ui="{ thead: 'hidden' }"
        >
          <template #year-data="{ row }">
            <span class="font-semibold">{{ row.year }}</span>
          </template>
          <template #school-data="{ row }">
            <span class="font-semibold">{{ row.school }}</span>
          </template>
          <template #logo-data="{ row }">
            <div class="flex justify-end items-center">
              <NuxtImg
                :src="row.logo"
                class="rounded-md"
              />
            </div>
          </template>
        </UTable>
      </UPageCard>

      <UPageCard
        title="Tarifs"
        icon="i-heroicons-currency-euro"
        class="mb-20 sm:mb-24"
      >
        <UTable
          class="mt-5"
          :rows="prices"
          :ui="{ thead: 'hidden' }"
        />

        <p class="text-sm text-gray-400 mt-3">
          Ces honoraires vous sont communiqués à titre indicatif par le praticien. Ils peuvent varier selon le type de soins finalement réalisés en cabinet, le nombre de consultations et les actes additionnels nécessaires.
        </p>
      </UPageCard>
    </UPage>
  </UContainer>
</template>

<script setup lang="ts">
const { data: page } = await useAsyncData('contact', () => queryContent('/contact').findOne())
if (!page.value) {
  throw createError({ statusCode: 404, statusMessage: 'Page not found', fatal: true })
}

useSeoMeta({
  title: page.value.title,
  ogTitle: page.value.title,
  description: page.value.description,
  ogDescription: page.value.description
})

const studies = [{
  year: '1991',
  title: 'Diplôme d\'état de Pédicure Podologue',
  school: 'ASSAS Paris',
  logo: '/assas_logo.png'
}, {
  year: '2001',
  title: 'Diabétologie',
  school: 'SALPETRIERE Paris',
  logo: '/salpetriere_logo.png'
}, {
  year: '2005',
  title: 'Podologie du sport',
  school: 'CINETIC SANTE Paris',
  logo: '/cinetic_logo.jpg'
}, {
  year: '2006',
  title: 'Posturologie',
  school: 'CINETIC SANTE Paris',
  logo: '/cinetic_logo.jpg'
}, {
  year: '2007',
  title: 'Podopédiatrie',
  school: 'CINETIC SANTE Paris',
  logo: '/cinetic_logo.jpg'
}, {
  year: '2015',
  title: 'Posturologie',
  school: 'BRICOT Paris',
  logo: '/bricot_logo.png'
}, {
  year: '2005',
  title: 'Posturologie',
  school: 'BRICOT Paris',
  logo: '/villier_logo.jpg'
}]

const prices = [{
  name: 'Soins de pédicure',
  price: '37€'
}, {
  name: 'Semelles orthopédiques',
  price: '80€ à 100€'
}, {
  name: 'Bilan podologique/posturologique',
  price: '55€ '
}, {
  name: 'Orthoplastie',
  price: '20€ à 60€'
}, {
  name: 'Réfléxologie',
  price: '55€'
}, {
  name: 'Orthonyxie',
  price: '20€'
}, {
  name: 'Soins à domicile',
  price: 'de 45€ à 50€'
}]
</script>
