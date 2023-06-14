<template>
  <HeaderApp />
  <div class="container py-4">
    <router-view> </router-view>
  </div>
<FooterApp />
</template>

<script>
    import HeaderApp from './components/HeaderApp.vue';
    import FooterApp from './components/FooterApp.vue';
    export default{
       name : 'App',
       components : 
       {
        HeaderApp,
        FooterApp
       }
    }
</script>