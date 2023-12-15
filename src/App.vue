<template>
  <div>
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <EmployView></EmployView>
  </div>
</template>

<script>
import EmployView from './components/EmployView.vue'

export default {
  name: 'App',
  components: {
    EmployView
  }
}
</script>

