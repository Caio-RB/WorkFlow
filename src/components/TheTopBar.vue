<script>

</script>

<template>
  <header class="header">
				<img src="../assets/logo.png" class="header__logo">
				<a class="menu__click"><i class="bx bx-menu bx-md" undefined ></i></a>
		</header>
</template>
<style>
.header{
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