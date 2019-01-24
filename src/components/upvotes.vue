<template>
  <div class="container">
    <h2 class="text-center">UpVote!</h2>
    <br><br>
    <div v-for="submission in submissions">
      <app-upvote  :data="submission" :key="submission.id"></app-upvote>
    </div>

  </div>
</template>

<script>
  import Upvote from './upvote.vue';
  import {submissions} from './../seed.js';
  import {eventBus} from './../eventBus.js';
export default {
  data(){
    return {
      submissions: submissions
    }
  },
  methods: {
    // upvote(data){
    //   console.log(data);
    //   let submission = this.submissions.find( submission => {
    //     return submission.id = data;
    //   });
    //     console.log(submission);
    // }
  },
  components: {
    'app-upvote': Upvote
  },
  created() {
    eventBus.$on('increment', (id) =>{
      console.log(id);
      let submission = this.submissions.find( submission => {
        return submission.id == id;
      });
      submission.votes++;
      console.log(submission);
    });
  }
}
</script>

<style scoped>

</style>
