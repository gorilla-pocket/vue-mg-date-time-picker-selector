# vue-mg-date-time-picker-selector

![npm](https://img.shields.io/npm/v/vue-mg-date-time-picker-selector)
![npm](https://img.shields.io/npm/dm/vue-mg-date-time-picker-selector)

## Installation

```
npm i vue-mg-date-time-picker-selector
```

## Usage

app.js

```javascript
import DateTimePickerSelector from 'vue-mg-date-time-picker-selector'
Vue.component('DateTimePickerSelector', DateTimePickerSelector)
```

Example:

```html
<template>
  <section class="container">
    <date-time-picker-selector v-model="date"/>
    <div>date: {{date}}</div>
  </section>
</template>

<style lang="scss" scoped>
</style>

<script>
export default {
  data() {
    return {
      show: false,
    }
  },
}
</script>
```

## License

MIT
