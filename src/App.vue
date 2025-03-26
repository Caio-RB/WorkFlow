<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
    <header>
				<img src="../src/assets/logo.png" class="header__logo">
				<a class="menu__click"><i class="bx bx-menu bx-md" undefined ></i></a>
		</header>

  <footer class="menu__container">
               <nav class="menu">
                    <ul class="menu__list">
                        <li class="menu__item"><RouterLink to="/" class="menu__link"><i class="bx bx-home bx-xs"></i>inicio</RouterLink></li>
                        <li class="menu__item"><RouterLink to="/drugs" class="menu__link"><i class="bx bx-capsule bx-xs"></i>drogas</RouterLink></li>
                        <li class="menu__item"><RouterLink to="/report" class="menu__link"><i class="bx bx-clipboard bx-xs"></i>relatório</RouterLink></li>
                        <li class="menu__item"><RouterLink to="/material" class="menu__link"><i class="bx bx-box bx-xs"></i>material</RouterLink></li>
                        <li class="menu__item"><RouterLink to="/contact" class="menu__link"><i class="bx bx-phone bx-xs"></i>ramal</RouterLink></li>
                    </ul>
                </nav>
        </footer>

  <RouterView />
</template>

<style scoped>
.menu{
    width: 100%;
    height: 100%;
}
.menu__list{
    width: 100%;
    height: 100%;
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-evenly; 
    align-items: center; 
}
.menu__item{
    text-transform: capitalize;
}

.menu__link:link, .menu__link:visited{
    color: var(--disabled-link-color);
}

.menu__link:hover, .menu__link:active{
    color:var(--active-link-color);
}

.menu__container{
	width:100vw;
	height:10vh;
	background-color:var(--primary-color);
	color:var(--tertiary-color);
    display: flex;
    overflow: hidden;
    position: absolute;
    bottom: 0;
}

header{
    background-color: var(--tertiary-color);
    width: 100%;
    height:12vh;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.75);
    -webkit-box-shadow: 0 4px 8px rgba(0, 0, 0, 0.75);
    -moz-box-shadow: 0 4px 8px rgba(0, 0, 0, 0.75);
    display: flex;
    flex-flow: row wrap;
    align-items: center;
    overflow: hidden;
    justify-content: space-around;
}

.header__logo{
  width:8rem; 
}

</style>
