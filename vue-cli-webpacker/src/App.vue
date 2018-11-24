<template>
  <div class="container">
    <div class="">
      <project-list/>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import ProjectList from './components/ProjectList'

export default {
  name: 'App',
  components: {
    HelloWorld,
    ProjectList
  }
}
</script>

<style lang="scss">
@import '../node_modules/bootstrap/scss/bootstrap.scss';
</style>
