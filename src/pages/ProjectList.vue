<template>
    <div class="container">
        <h1>{{ title }}</h1>
        <div class="row">
            <div class="col mx-3" v-for="(project, index) in projects" :key="project.id">
                <div class="card" style="height:400px">
                    <div class="card-title">
                        <h3>{{ project.name }}</h3>
                    </div>
                    <div class="card-img-top">
                        <img class="img-fluid" :src="project.image" :alt="project.name">
                    </div>
                    <p class="card-text">
                        <router-link :to="{name : 'single-project' , params:{slug: project.slug}}" class="btn btn-primary">
                            Check Project
                        </router-link>
                    </p>
                </div>
            </div>
        </div>
        <nav aria-label="Page navigation example">
            <ul class="pagination">
                <li class="page-item"><button :class="{ 'page-link': true, 'disabled': currentPage === 1 }"
                        @click="getData(currentPage - 1)">Previous</button></li>
                <li class="page-item" v-for="n in lastPage"><button
                        :class="{ 'page-link': true, 'active': currentPage === n }" @click="getData(n)">{{ n }}</button>
                </li>

                <li class="page-item"><button :class="{ 'page-link': true, 'disabled': currentPage === lastPage }"
                        @click="getData(currentPage + 1)">Next</button></li>
            </ul>
        </nav>
    </div>
</template>

<script>
import axios from 'axios';

export default {
  'name' : 'ProjectList',
  data(){
    return {
      title: 'Portfolio',
      projects : [],
      apiUrl: 'http://127.0.0.1:8000/api',
      currentPage: 1,
      lastPage: null
    };
  },
  methods: {
        getData(numPage) {
            axios.get(`${this.apiUrl}/projects`, {
                params: {
                    'page': numPage
                }
            }).then((res) => {
                //console.log(res);
                this.projects = res.data.results.data;
                this.currentPage = res.data.results.current_page;
                this.lastPage = res.data.results.last_page;
            })
        }
    },
    mounted() {
        this.getData(1);
    }
}
</script>