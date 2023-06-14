<template>
  <HeaderApp />
  <div class="container py-4">
    <router-view> </router-view>
  </div>
</template>

<script>
    import HeaderApp from './components/HeaderApp.vue';
    export default{
       name : 'App',
       components : 
       {
        HeaderApp
       }
    }
</script>