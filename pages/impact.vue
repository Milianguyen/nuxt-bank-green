<template>
  <div class="page">
    <div class="bg-sushi-50">
      <div class="page-fade-in contain pt-28 pb-16">
        <div
          class="prose mx-auto max-w-4xl text-center prose-headings:font-semibold"
        >
          <PrismicRichText
            v-if="impact?.data.text1"
            :field="impact?.data.text1"
          />
          <h1 v-else>Opened an account with a bank that doesn't finance fossil fuels?</h1>
          <PrismicRichText
            v-if="impact?.data.text2"
            class="mt-0"
            :field="impact?.data.text2"
          />
          <h2 class="mt-0" v-else>Maximise your impact by letting us know.</h2>
          <PrismicRichText
            :field="impact?.data.text3"
            fallback="Taking this survey helps advocate for change. Bank.Green uses your
            response to push fossil banks to divest, push sustainable eco banks to improve their
            customer experience, and encourage other people to join you in greening their finances."
          />
          <SwitchForm :opts="{ height: 600 }" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const { client } = usePrismic()
const { data: impact } = await useAsyncData('impact', () =>
  client.getByUID('textonlypages', 'impactpage'))
useHead({
  title: 'Take Our Fossil Free Banking Survey - Maximize Your Impact',
  htmlAttrs: {
    lang: 'en'
  },
  link: [
    {
      hid: 'canonical',
      rel: 'canonical',
      href: 'https://bank.green/impact'
    }
  ],
  meta: [
    { property: 'og:locale', content: 'en_US' },
    { property: 'og:type', content: 'website' },
    { property: 'og:site_name', content: 'Bank Green' },
    { property: 'og:url', content: 'https://bank.green/impact' },
    { name: 'description', content: 'Maximize your impact by letting us know you opened an account with a bank that doesn\'t finance fossil fuels.' }
  ]
})
</script>
