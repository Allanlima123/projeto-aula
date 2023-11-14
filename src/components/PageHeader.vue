<template>
  <header class="container_header">
    <div class="box_info">
      <h2>Olá, {{ nome }}</h2>
      <p>Aqui estão as informações sobre suas vendas.</p>
    </div>

    <div class="box_info_user">
      <div class="box_icon">
        <i class="fa-regular fa-bell"></i>
      </div>

      <div class="box_icon">
        <i class="fa-solid fa-magnifying-glass"></i>
        <span class="notification"></span>
      </div>

      <div class="box_img">
        <img :src="url_image" alt="imagem user" />
      </div>

      <h3>{{ nome }} {{ sobreNome }}</h3>
    </div>
  </header>
</template>

<script>
import axios from 'axios';

export default {
  name : "PageHeader",
  data(){
    return{
      url_image : String,
      nome : String,
      sobreNome : String
    }
  },
  methods: {
    async getDataUser(){
      try{
        const dataFetch = await axios.get('http://localhost:3000/Perfil_Usuario')
        this.nome = dataFetch.data.nome;
        this.url_image = dataFetch.data.image_perfil;
        this.sobreNome = dataFetch.data.sobre_Nome;
        
      }catch(ERROR){
        console.error('Erro ao buscar dados do usuário:', ERROR);
      }

    }
  },

  mounted(){
    this.getDataUser()
  }
};
</script>

<style scoped>
.container_header{
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 5rem;
}

.container_header .box_info{
  font-family: var(--main-font);
  font-size: 1.3rem;
  color: var(--dark);
  font-weight: 500;
  font-style: normal;
}

.container_header .box_info h2{
  margin-bottom: .5rem;
}

.container_header .box_info p{
  color: var(--gray);
}

.container_header .box_info_user{
  display: flex;
  align-items: center;
}

.container_header .box_info_user .box_icon{
  color: var(--dark);
  font-size: 1.8rem;
  margin-left: 1.2rem;
  cursor: pointer;
  position: relative;
}

.container_header .box_info_user .box_icon .notification{
  position: absolute;
  right: -.1rem;
  top: -.5rem;
  width: .6rem;
  height: .6rem;
  border: .1rem solid var(--light-purple);
  border-radius: 50%;
}

.container_header .box_info_user .box_img{
  margin-left: 2rem;
  width: 3.5rem;
  height: 3.5rem;
  border-radius: 50%;
  overflow: hidden;
}

.container_header .box_info_user .box_img img{
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.container_header .box_info_user h3{
  margin-left: 1rem;
  font-family: var(--main-font);
  color: var(--dark);
  font-size: 1.3rem;
}
</style>