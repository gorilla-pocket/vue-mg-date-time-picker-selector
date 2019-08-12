<template>
  <section class="container">
    <date-time-picker-selector v-model="date"/>
    <div>date: {{date}}</div>
  </section>
</template>

<style lang="scss" scoped>
</style>

<script>
import DateTimePickerSelector from '../src/vue-mg-date-time-picker-selector'
import 'bootstrap'
import 'bootstrap/dist/css/bootstrap.min.css'
export default {
  data() {
    return {
      date: '',
    }
  },
  methods: {
    ///
  },
  components: {
    DateTimePickerSelector,
  },  
}
</script>