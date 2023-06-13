<template>
    <div class="container">
        <h1>{{ title }}</h1>
        <div class="row">
            <div class="col" v-for="(project, index) in projects" :key="project.id">
                <div class="card" style="width:200px">
                    <div class="card-title">
                        <h3>{{ project.name }}</h3>
                    </div>
                    <div class="card-img-top">
                        <img class="img-fluid" :src="project.image" :alt="project.name" class="img-fluid">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
  'name' : 'App',
  data(){
    return {
      title: 'Ciao',
      projects : [],
      apiUrl: 'http://127.0.0.1:8000/api'
    };
  },
  methods: {
    getData() {
      axios.get(`${this.apiUrl}/projects`).then((res) => {
        this.projects = res.data.results.data;
      });
    }
  },
  mounted() {
    this.getData();
  }
}
</script>