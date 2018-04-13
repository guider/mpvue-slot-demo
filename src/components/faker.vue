<template lang="pug">
  form(@submit="formSubmit" report-submit="true")
    slot
</template>

<script>
  export default {
    components: {},
    data() {
      return {}
    },
    methods: {
      formSubmit(e) {
        console.log(e);
        this.$emit('fakerClick',e.target.formId)
      }
    },
    computed: {},
    mounted() {

    }
  }
</script>

<style lang="less">


</style>
