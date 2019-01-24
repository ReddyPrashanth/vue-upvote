<template>
  <div class="card col-md-6 offset-md-3 mb-4" :class="{'border-primary': data.votes >= 20, 'border-warning': data.votes <20 }">
    <div class="card-body pb-0">
      <div class="media">
        <img src="./../assets/images/picture.png" class="mr-3" alt="picture">
        <div class="media-body">
          <h5 class="mt-0 text-warning">{{data.title}}
            <span class="badge badge-light">#{{data.id}}</span>
          </h5>
          {{data.description}}
          <p class="small">Submitted By:
            <img :src="data.avatar" class="img-fluid" style="width: 24px; height: 24px" alt="user">
          </p>
        </div>
        <div>
       <span class="float-right" @click="inc(data.id)">
        <i class="fas fa-chevron-up"></i>
        <strong class="text-info">{{data.votes}}</strong>
      </span>

        </div>
      </div>
    </div>
  </div>

</template>

<script>
  import {eventBus} from './../eventBus.js';
export default {
  props: ['data'],
  methods: {
    inc(id) {
      console.log(id);
      eventBus.$emit('increment', id);
    }
  }
}
</script>

<style scoped>

</style>

