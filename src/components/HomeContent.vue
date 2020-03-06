<template>
  <div class="next-steps" v-if="tasks.length>0">
    <h2 class="my-5 text-center">HERE'S YOUR TASKS</h2>

    <div class="row">
      <div class="col-md-8 mb-4" v-for="task in tasks" :key="task._id">
        <h6 class="mb-3">
          <router-link :to="{ name: 'data', params: { task:task }}">{{task.name}}</router-link>


        </h6>
        <p>{{task.details}}</p>
      </div>

      <div class="col-md"></div>


    </div>
  </div>
  <div class="next-steps" v-else>
    <h2 class="my-5 text-center">YOU HAVE NO TASKS</h2>

  </div>
</template>

<script>
  import axios from 'axios';
export default {
  name: "HomeContent",
  data(){
    return {
      token: undefined,
      tasks:[]
    }

  },

  methods: {
    getToken() {
      return this.token;
    }
  },
  async mounted() {
    const token = await this.$auth.getIdTokenClaims();
    const resp = await axios.get('https://kvh82qk4wb.execute-api.us-west-2.amazonaws.com/develop/v1/api/tasks',
            {
              headers: {
                "Authorization": `Bearer ${token.__raw}`
              }
            });
    this.tasks = resp.data.message;

    // eslint-disable-next-line no-console
    console.log('resp',resp);

    // eslint-disable-next-line no-console
    console.log('token', token.__raw);

    this.token= token.__raw || 'no token';


  },

};
</script>
