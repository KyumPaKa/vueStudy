<template>
  <div id="root">
      <p>{{ originalPrice }}</p>
      <p>{{ doublePrice }}</p>
      <p>{{ triplePrice }}</p>
  </div>
</template>

<script>
import { mapGetters } from 'vues';

export default {
    computed: {
        ...mapGetters(['originalPrice', 'doublePrice', 'triplePrice'])
        
        // originalPrice() {
        //     return this.$store.getters.originalPrice;
        // },
        // doublePrice() {
        //     return this.$store.getters.doublePrice;
        // },
        // triplePrice() {
        //     return this.$store.getters.triplePrice;
        // }
    }
}
</script>

<style>

</style>