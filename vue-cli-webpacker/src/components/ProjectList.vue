<template lang="html">
  <div class="b-project-list">
    <h2>Proyectos</h2>
    <div class="b-project" v-for="project in projects">
      <h3 class="b-project__title">{{ project.title }}</h3>
      <div class="b-project__description">
        {{ project.description }}
      </div>
      <div class="b-project__created-at">
        <!-- {{ project.created_at | formatDate('DD MMM YYYY') }} -->
        {{ project.created_at }}
      </div>
      <div class="b-project__actions">
        <a href="#" class="btn btn-danger" v-on:click="deleteProject(project)">Eliminar proyecto</a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'project-list',
  data() {
    return { projects: [] }
  },
  methods: {
    deleteProject: function(project) {
      console.warn("Eliminar project", project)
    }
  },
  filters:{
    formatDate: (date, outputFormat) => {
      return moment(date).format(outputFormat);
    }
  },
  mounted: function() {
    const serverURL = 'http://172.104.91.187/projects'

    const configAxios= {
      url: serverURL,
      method: 'get',
      responserType: 'json',
      data: {},
      headers: {
        'Content-Type': 'application/json',
        'Api-Token': 'jJHGtk3IoZ84CmKlDz5N206w46yaj6v4mk0vXdTDl5w80iqnk0skp9Jp6NQ3'
      }
    };
    axios.request(configAxios).then((response) => {
      console.log(response);
      this.projects = response.data;
    });
  }
}
</script>

<style lang="css">
body {
    color: #000;
    background-color: #f2f2f2;
}

a {
    color: #1abc9c;
}

a:hover {
    color: #1abc9c;
}

[v-cloak] {
    display: none;
}

.b-project-list {
    border-top: 1px solid #1abc9c;
    border-left: 1px solid #ccc;
    border-right: 1px solid #ccc;
    border-bottom: 1px solid #ccc;
    background: white;
    padding: 20px;
    margin-top: 20px;
}

.b-project {
    overflow: hidden;
    border-bottom: 1px dashed #ccc;
    padding-bottom: 10px;
}

.b-project__title {
    font-size: 18px;
    color: #1abc9c;
    line-height: 1.5em;
}

.b-btn-new-project {
    height: 40px;
}

.b-project__actions {
    margin-top: 10px;
    background: #f1f1f1;
    padding: 10px 15px 6px 15px;
}

.b-project__actions .fa {
    color: #000;
    font-size: 20px;
}

.b-project__actions .fa:hover {
    color: #1abc9c;
    cursor: pointer;
}
</style>
