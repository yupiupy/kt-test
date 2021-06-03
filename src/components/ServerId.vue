<template>
    <option id="server_id" :value="item.buy" >{{ item.ccy }}</option>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      reqired: true
    }
  }
}
</script>
