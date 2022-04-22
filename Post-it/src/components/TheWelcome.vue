<script>
import {
    RouterLink,
    RouterView
} from 'vue-router'
export default {
   
name :"the welcome",
    data: function () {
        return {
            results: [],
        }
    },
    mounted() {
        const url = "http://5.135.119.239:3090/notes";
        fetch(url)
            .then(response => response.json())
            .then(data => {
                this.results = [...data.notes];
            });
    },
    methods : {deletePostit: function (id) {const url = "http://5.135.119.239:3090/notes/" + id;fetch(url, {method: "DELETE",}).then((response) => response.json()).then((data) => {this.results = data.note;}).then(() => {window.location.reload();});},},
}
</script>

<template>




<div>
   
     
   
    

    <!-- <nav>
       
        <router-link to="/TabA">Add Post-it</router-link>
    </nav> -->

    <link href="https://fonts.googleapis.com/css2?family=Reenie+Beanie&display=swap" rel="stylesheet">
    <ul>
        <li v-for="(result,idx) in results" v-bind:key="idx">
            <a :href="'/notes/' + result._id">
                <h1>{{result.title}}</h1>
                <p v-for="(content,i) in result.content" v-bind:key="i">

                    {{content}}
                </p>
        

            </a>
            <button type="button" class="fa fa-trash-o" v-on:click="deletePostit(result._id)"></button>


        </li>
    </ul>
</div>
</template>

<style scoped>
@import '@/assets/base.css';
body {
    margin: 20px auto;
    font-family: 'Lato';
    
    font-size: 12px;
    
}
* {
    margin: 0;
    padding: 0;
}
h2 {
    font-weight: bold;
    font-size: smaller;
    
}
h1 {
    font-weight: bold;
    font-size: 10px;
}
p {
    /* font-family: 'Reenie Beanie'; */
    font-size: 1rem;
    text-align: left;
}
ul,
li {
    list-style: none;
    
}
ul {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}
ul li a {
    text-decoration: none;
    color: #000;
    
    display: block;
    height: 10em;
    width: 10em;
    padding: 1em;
    box-shadow: 5px 5px 7px rgba(33, 33, 33, .7);
    transform: rotate(-6deg);
    transition: transform .15s linear;
}
ul li:nth-child(even) a {
    transform: rotate(4deg);
    position: relative;
    top: 5px;
    background: #cfc;
    
    
}
ul li:nth-child(3n) a {
    transform: rotate(-3deg);
    position: relative;
    top: -5px;
    background: #ccf;
    
}
ul li:nth-child(5n) a {
    transform: rotate(5deg);
    position: relative;
    top: -10px;
}
ul li a:hover,
ul li a:focus {
    box-shadow: 10px 10px 7px rgba(0, 0, 0, .7);
    transform: scale(1.25);
    position: relative;
    z-index: 5;
}
ul li a {
    text-decoration: none;
    color: #000;
    background: #ffc;
    display: block;
    height: 10em;
    width: 10em;
    padding: 1em;
    box-shadow: 5px 5px 7px rgba(33, 33, 33, .7);
    transition: transform .15s linear;
}
ul li {
    margin: 1em;
}
#app {
    max-width: 1280px;
    margin: 0 auto;
    padding: 2rem;
    font-weight: normal;
    
}
header {
    line-height: 1.5;
    max-height: 100vh;
    
}
.logo {
    display: block;
    margin: 0 auto 2rem;
}
a,
.green {
    text-decoration: none;
    color: rgb(35, 160, 118);
    transition: 0.4s;
    
}
@media (hover: hover) {
    a:hover {
        background-color: hsla(160, 100%, 37%, 0.2);
    }
}
nav {
    width: 100%;
    font-size: 10px;
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
h2 {
    font-weight: bold;
    font-size: 2rem;
    
    
}
p {
    font-family: 'Reenie Beanie';
    font-size: 1rem;
    color: black;
     
}
ul li a {
    transform: rotate(-6deg);
    
}
@media (min-width: 1024px) {
    body {
        display: flex;
        place-items: center;
        
        
       
        
    }
    #app {
      
        padding: 0 2rem;
        
        
    }
    header {
        display: flex;
        place-items: center;
        padding-right: calc(var(--section-gap) / 2);
    }
    header .wrapper {
        display: flex;
        place-items: flex-start;
        flex-wrap: wrap;
        background-color: aquamarine;
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
}
</style>