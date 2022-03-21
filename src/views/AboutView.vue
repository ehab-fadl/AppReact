<template>
  <div class="about">
    <h1 class="h1Style">Welcome to Vue.js page</h1>

      <table class="table table-hover table-dark">
  <thead>
    <tr>
      <th>Title</th>
      <th>Author</th>
      <th>Number of Pages</th>
      <th>Publish date</th>
       <th>Download</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="item in list" :key="item.id">
      <th>{{item.Tirle}}</th>
      <td>{{item.Author}}</td>
      <td>{{item.NumberOfPages}}</td>
      <td>{{item.PublishesAt}}</td>
       <td><a v-bind:href="item.Link"><button class="btn btn-info">Download</button></a></td>
    </tr>
    
  </tbody>
</table>


  </div>
</template>



<script>
import Vue from 'vue';
import axios from 'axios';
import VueAxios from 'vue-axios';

Vue.use(VueAxios,axios);

export default {
  name: 'AboutView',
  components: {
   
  },
  data(){
    return {list:undefined}
  },
  //THB//http://192.168.0.100:6555/api/books
  mounted(){
    Vue.axios.get('http://192.168.0.10:8888/api/books').then(resp=>{
     this.list=resp.data;
      
    })
  }
  
}
</script>

<style>
.h1Style{

  color:darkorange;
  font-size: 70px;
  margin-bottom: 20px;
}
</style>