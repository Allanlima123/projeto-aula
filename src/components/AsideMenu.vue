<template>
  <aside class="container_aside">
    <h1 class="box_title">
        <strong>h</strong>ellodev
    </h1>

    <nav class="nav_bar">
      <ul class="list_itens">
        <li class="item item_dashboard">
          <a href="#">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="22"
              height="22"
              
              fill="none"
            >
              <path
                d="M21 14H14V21H21V14Z"
                stroke="#9E6EFE"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M10 14H3V21H10V14Z"
                stroke="#9E6EFE"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M21 3H14V10H21V3Z"
                stroke="#9E6EFE"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M10 3H3V10H10V3Z"
                stroke="#9E6EFE"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
            Dashboard</a
          >
        </li>
        <li class="item">
          <a href="#">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="20"
              height="18"
              viewBox="0 0 20 18"
              fill="none"
            >
              <path
                d="M6 4H3C1.89543 4 1 4.89543 1 6V15C1 16.1046 1.89543 17 3 17H17C18.1046 17 19 16.1046 19 15V6C19 4.89543 18.1046 4 17 4H14M13 8L10 11M10 11L7 8M10 11L10 1"
                stroke="#2D3748"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
            Carteira
          </a>
        </li>
        <li class="item">
          <a href="#">
            <i class="fa-solid fa-cart-shopping"></i>
            Transações
          </a>
        </li>
        <li class="item">
          <a href="#">
            <i class="fa-solid fa-user-group"></i>
            Suporte
          </a>
        </li>

        <hr>

        <li class="item item_ajustes">
          <a href="#">
            <i class="fa-solid fa-gear"></i>
            Ajustes
          </a>
        </li>
        <li class="item item_desconectar">
          <a href="#">
            <i class="fa-solid fa-power-off"></i>
            Desconectar
          </a>
        </li>
      </ul>
    </nav>
  </aside>
</template>

<script>
export default {};
</script>

<style scoped>

hr{
    margin: 0 3rem;
    color: var(--dark);
}
.container_aside {
  min-height: 100vh;
  width: 25rem;
  background: var(--white);
  border-radius: 0 2.6rem 2.6rem 0;
  box-shadow: 1.5rem .7rem 1rem -7px rgba(0, 0, 0, 0.1);
}

.box_title{
    text-align: center;
    padding: 35px 0 45px 0;
    font-family: var(--main-font);
    font-size: 3.2rem;
    font-weight: 600;
    cursor: pointer;
}

.box_title strong{
    text-transform: capitalize;
    color: var(--light-purple);
}

.nav_bar .list_itens .item {
    padding: 1rem 1rem 1rem 2.5rem;
    margin-bottom: 3rem;
    font-size: 1.9rem;
    font-weight: 40rem;
}

.nav_bar .list_itens .item a{
    font-family: var(--main-font);
    color: var(--dark);
    padding: 1.8rem;
}

.nav_bar .list_itens .item a svg,
.nav_bar .list_itens .item a {
    color: var(--dark);
    margin-right: 1rem;
}

.nav_bar .list_itens .item_dashboard a{
    margin-bottom: 5.3rem;
    background: rgba(158, 110, 254, 0.06);
    color: var(--light-purple);
}

.nav_bar .list_itens .item_ajustes{
    margin-top: 4rem;
    margin-bottom: 4rem;
}

.nav_bar .list_itens .item_dashboard a,
.nav_bar .list_itens .item_desconectar a{
    border-radius: .6rem;
}

.nav_bar .list_itens .item_desconectar a{
    background: rgba(240, 61, 61, 0.06);
    color: var(--error);
}

</style>