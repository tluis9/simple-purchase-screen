<template>
  <purchase-screen />
</template>

<script>
import PurchaseScreen from './components/PurchaseScreen.vue'
export default {
  components: {
    PurchaseScreen
  },
  props: {
    source: String
  },
};
</script>
