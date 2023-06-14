<template>
        <div v-if="project" class="card p-3">
                        <div class="card-title">
                            <h3>{{ project.name }}</h3>
                        </div>
                        <div>
                            <div class="card-img-top">
                                <img class="img-fluid" :src="project.image" :alt="project.name" style="height:300px">
                            </div>
                            <div class="py-4">
                                <p>
                                    Type: {{ project.type.name }}
                                </p>
                                <p>
                                    Technologies used: 
                                </p>
                                <ul>
                                    <li v-for="tech in project.technologies">
                                        {{ tech.name }}
                                    </li>
                                </ul>
                            </div>
                        </div>
        </div>
        <div v-else>
            <LoaderApp />
        </div>
</template>

<script>
    import axios from 'axios';
    import LoaderApp from '../components/LoaderApp.vue';

    export default{
       name : 'SingleProject',
       data() {
        return {
            project: null,
            apiUrl: 'http://127.0.0.1:8000/api'
        }
       },
       components : 
       {
        LoaderApp
       },
       methods: {
        getProject() {
            axios.get(`${this.apiUrl}/projects/${this.$route.params.slug}`).then((res)=> {
                if(res.data.success){
                    this.project = res.data.results;
                }
                else
                {
                    this.$router.push( {name: 'not-found'});
                }
            })
        }
       },
       mounted(){
        this.getProject();
       }
    }
</script>