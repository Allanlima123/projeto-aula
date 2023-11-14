<template>
  <AsideMenu />
  <PageDashboard />
  <router-view/>
</template>

<script>
import AsideMenu from './components/AsideMenu.vue';
import PageDashboard from './components/Dashboard/PageDashboard.vue';

export default {
  name : "App",
  data(){},
  components:{
    AsideMenu,
    PageDashboard
  }
};
</script>

<style>
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css');

:root{
  --main-font:'Popping', sans-serif;
  --message:#2962FF;
  --success:#0BB07B;
  --warning:#FFCE52;
  --error: #F03D3D;
  --information:#E0E0E0;
  --dark:#2D3748;
  --gray:#718096;
  --light-gray:#F9F9F9;
  --white:#FFFFFF;
  --light-purple:#9E6EFE;
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  outline: none;
  list-style: none;
  text-decoration: none;
}

#app{
  display: flex;
  background: #F3F4F8;
}

html{
  font-size: 62.5%;
  scroll-behavior: smooth;
}
</style>
