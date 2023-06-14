<template>
    <div class="jumbotron p-5 mb-4 rounded-3">
    <div class="container py-5">
        <div class="text-center">
            <h1 class="display-5 fw-bold text-center">
                Hi! My name is
            </h1>
            <img src="../images/glumia-logos_black.png" alt="" width="400">
        </div>
        <div class="text-center mt-4">
            <p>
                and this is my portfolio
            </p>
        </div>
            <div class="homepage d-flex justify-content-center gap-3">
                <router-link :to="{name : 'projects' }" class="btn btn-primary">
                            Check my Projects
                </router-link>
                <router-link :to="{name : 'projects' }" class="btn btn-primary">
                            Create a new project
                </router-link>
                <router-link :to="{name : 'about-us' }" class="btn btn-primary">
                            About me
                </router-link>
            </div>
    </div>
</div>
</template>

<script>
    export default{
        name: 'HomePage'
    }
</script>