<script setup>

import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from '@/components/HelloWorld.vue'
</script>

<template>
  <!-- <img src="Post - it/png" /> -->
  <link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.3.0/css/font-awesome.min.css" rel="stylesheet">
  <header>
   

    <div class="wrapper">

   

      <nav>
        <RouterLink to="/"><H1> Welcome to Post-it  </H1>  </RouterLink>
        <RouterLink to="/CreatePostIt">ADD Post-It</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
  
<!-- header here  -->

</template>

<style>


:-webkit-any(article, aside, nav, section) h1 {
    font-size: 3.5em;
    margin-block-start: 0em;
    margin-block-end: 0em;}

@import '@/assets/base.css';

#app {
    max-width: 1280px;
    margin: 250px;
    padding: 100 px;
  

    font-weight: normal;
}

header {
    line-height: 1.5;
    max-height: 100vh;
    position:absolute;
    top: 0px;
    
    
}



.logo {
    display: block;
    margin: 0 auto 2rem;
}

a,
.green {
    text-decoration: none;
    color: hsla(160, 100%, 37%, 1);
    transition: 0.4s;
}

@media (hover: hover) {
    a:hover {
        background-color: hsla(160, 100%, 37%, 0.2);
    }
}

nav {
    width: 100%;
    font-size: 12px;
    text-align: center;
    margin-top: 2rem;
}

nav a.router-link-exact-active {
    color: var(--color-text);
}

nav a.router-link-exact-active:hover {
    background-color: transparent;
}

nav a {
    display: inline-block;
    padding: 0 1rem;
    border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
    border: 0;
}

body {
       
         background: linear-gradient(blue,pink);
         height: 100%;
         width: 100%;
    }

@media (min-width: 1024px) {
    body {
        display: grid;
        place-items: center;
        background: linear-gradient(blue,pink);
         background: linear-gradient(blue,pink);
    }

    #app {
       
        padding: 0 2rem;
    }

    header {
        display: grid;
        place-items: center;
        padding-right: calc(var(--section-gap) / 2);
        
        
    }

    header .wrapper {
        display: flex;
        place-items: flex-start;
        flex-wrap: wrap;
        
    }

    .logo {
        margin: 0 2rem 0 0;
    }

    nav {
        text-align: left;
        margin-left: -1rem;
        font-size: 1rem;
        padding: 1rem 0;
        margin-top: 1rem;
       
    }

    .wrapper{
        margin-top:50px;

    }
    
}

</style>
