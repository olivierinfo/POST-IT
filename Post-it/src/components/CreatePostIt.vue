<template>
<div class="template">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    <div id="app" class="container">
        <div id="post-it" class="card">
            <div class="card-header">
              
                <h3>Welcome to the space for creating a Post-it</h3>
            </div>

            <div class="card-body">
                <div class="form-group">
                    <input type="text" class="form-control" ref="post_title" placeholder="Post-title" />
                </div>

                <div class="form-group">
                    <input type="text" class="form-control description" ref="post_description" placeholder="Description" />
                </div>

                <button class="btn btn-sm btn-primary" @click="postData">Create Post-It</button>
                <button class="btn btn-sm btn-warning ml-2" @click="clearPostOutput">Delete</button>
                <div v-if="postResult" class="alert alert-secondary mt-2" role="alert">
                    <pre>{{postResult}}</pre>
                </div>
            </div>
        </div>
    </div>
    
</div>

</template>

<script>

function myFunction() {
  alert("I am an alert box!");
}

const baseURL = "http://5.135.119.239:3090/notes/";
export default {
    name: " CreatePostIt",
    data() {
        return {
            postResult: null
        }
    },
    methods: {
        fortmatResponse(res) {
            return JSON.stringify(res, null, 2);
        },
        async postData() {
            const postData = {
                title: this.$refs.post_title.value,
                content: this.$refs.post_description.value,
            };
            try {
                
                const res = await fetch(`${baseURL}`, {
                    method: "post",
                    headers: {
                        "Content-Type": "application/json",
                        "x-access-token": "token-value",
                    },
                    body: JSON.stringify(postData),
                });
                if (!res.ok) {
                    const message = `An error has occured: ${res.status} - ${res.statusText}`;
                    throw new Error(message);
                }
                const data = await res.json();
                const result = {
                    status: res.status + "-" + res.statusText,
                    headers: {
                        "Content-Type": res.headers.get("Content-Type"),
                        "Content-Length": res.headers.get("Content-Length"),
                    },
                    data: data,
                };
                this.postResult = this.fortmatResponse(result);
            } catch (err) {
                this.postResult = err.message;
            }
        },
        clearPostOutput() {
            console.log(1, "je rentre dans la fonction effacer")
            this.postResult = null;
            console.log(this.postResult)
        },
    }
}
</script>

<style>
#app {
    padding: 0%;
}
.container {
    min-width: 100%;
}
.description {
    min-height: 150px;
}
#post-it {
    margin: 0 auto;
    width: 100%;
    height: 50%;

}

</style>