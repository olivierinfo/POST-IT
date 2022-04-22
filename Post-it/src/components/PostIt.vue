<template>
<div>

    <h2>Post-it ID : {{$route.params.id}}</h2>

  

    

    <link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.3.0/css/font-awesome.min.css" rel="stylesheet">
    <div class="container bootstrap snippets bootdey">
        <div class="row">
            <ul class="notes">
                <li>
                    <div class="rotate-1 lazur-bg">
                       <h1>{{results.title }}</h1> 
                      <p v-for="(content,i) in results.content" v-bind:key="i">

                    {{content}}
                </p>
                    </div>
                </li>

            </ul>
        </div>
    </div>

</div>
</template>

<script>
export default {

    name: 'PostIt',

    props: {

        msg: String

    },

    data: function () {

        return {

            results: [],

        }

    },

    mounted() {

        const url = "http://5.135.119.239:3090/notes/" + this.$route.params.id;

        fetch(url)

            .then(response => response.json())

            .then(data => {

                this.results = data.note;

                console.log(this.result)

            });

    },

    methods: {}

}
</script>

<style scoped>


body {
    margin-top: 20px;
    
}

ul.notes li {
    margin: 10px 40px 50px 0px;
    float: left;
}

ul.notes li,
ul.tag-list li {
    list-style: none;
}

ul.notes li div small {
    position: absolute;
    top: 5px;
    right: 5px;
    font-size: 10px;
}

div.rotate-1 {
    -webkit-transform: rotate(-6deg);
    -o-transform: rotate(-6deg);
    -moz-transform: rotate(-6deg);
}

div.rotate-2 {
    -o-transform: rotate(4deg);
    -webkit-transform: rotate(4deg);
    -moz-transform: rotate(4deg);
    position: relative;
    top: 5px;
}

.lazur-bg {
    background-color: #23c6c8;
    color: #ffffff;
}

.red-bg {
    background-color: #ed5565;
    color: #ffffff;
}

.navy-bg {
    background-color: #1ab394;
    color: #ffffff;
}

.yellow-bg {
    background-color: #f8ac59;
    color: #ffffff;
}

ul.notes li div {
    text-decoration: none;
    color: #000;
    display: block;
    height: 300px;
    width: 300px;
    padding: em;
    -moz-box-shadow: 5px 5px 7px #212121;
    -webkit-box-shadow: 5px 5px 7px rgba(33, 33, 33, 0.7);
    box-shadow: 5px 5px 7px rgba(33, 33, 33, 0.7);
    -moz-transition: -moz-transform 0.15s linear;
    -o-transition: -o-transform 0.15s linear;
    -webkit-transition: -webkit-transform 0.15s linear;
}
</style>
