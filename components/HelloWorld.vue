<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <!-- <v-img
          :src="require('@/assets/logo.png')"
          class="my-3"
          contain
          height="200"
        /> -->
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">Welcome to M1nPy</h1>

        <p class="subheading font-weight-regular">
          For help and collaboration with M1nPy,
          <br />please ask me via
          <a href="https://twitter.com/M1nPy" target="_blank">Twitter</a>
          Direct Message.
        </p>
      </v-col>

      <v-col class="mb-5" cols="12">
        <h2 class="headline font-weight-bold mb-3">Why am I me ?</h2>

        <v-row justify="center">
          <a
            v-for="(next, i) in whatsNext"
            :key="i"
            :href="next.href"
            class="subheading mx-3"
            target="_blank"
          >
            {{ next.text }}
          </a>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'HelloWorld',

  data: () => ({
    whatsNext: [
      {
        text: 'Wikipedia',
        href:
          'https://ja.wikipedia.org/wiki/%E3%81%AA%E3%81%9C%E7%A7%81%E3%81%AF%E7%A7%81%E3%81%AA%E3%81%AE%E3%81%8B',
      },
      {
        text: 'Amazon',
        href: 'https://www.amazon.co.jp/Why-Am-Me-Paige-Britt/dp/1338053140',
      },
      {
        text: 'Rakuten',
        href:
          'https://books.rakuten.co.jp/rk/c649e150ee46377098a3e86ab3264686/?l-id=item-c-relation-24',
      },
    ],
  }),
}
</script>
