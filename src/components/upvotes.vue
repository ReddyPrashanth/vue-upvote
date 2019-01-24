<template>
  <div class="container">
    <h2 class="text-center">UpVote!</h2>
    <br><br>
    <app-upvote v-for="submission in submissions" :data="submission" :key="submission.id" @increment="upvote"></app-upvote>
  </div>
</template>

<script>
  import Upvote from './upvote.vue';
  import {submissions} from './../seed.js';
export default {
  data(){
    return {
      submissions: submissions
    }
  },
  methods: {
    upvote(data){
      console.log(data);
      let submission = this.submissions.find( submission => {
        return submission.id = data;
      });
      submission.votes++;
    }
  },
  components: {
    'app-upvote': Upvote
  }
}
</script>

<style scoped>

</style>
