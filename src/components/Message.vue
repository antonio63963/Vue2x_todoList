<template>
  <div class="message">
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  props: {
    message: {
      type: String,
      required: false,
    },
  },
};
</script>

import
<style lang="scss" scoped>
p {
   color: #fc5c65;
   text-align: center;
}
    
</style>