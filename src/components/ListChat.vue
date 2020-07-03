<template>
  <div>
    <div class="" v-if="typeView === 0">
      <div class="col-md-11 text-center text-black-50 mt-3 ml-3" style="border-bottom: 3px solid green; height: 20%">
        <span><i class="fa fa-user fa-2x"></i></span>
        <h6>{{ name }}</h6>
      </div>
    </div>



      <div class="col-md-12" style="border-bottom: 2px solid #536e8a" v-else>
        <span><i class="fa fa-user fa-2x text-black-50"></i></span>
        <span class="pl-5 text-black-50 h5">{{ name }}</span>
        <span class="badge badge-pill badge-warning float-right p-2">1</span>
      </div>
  </div>
</template>

<script lang="ts">
  import {Component, Prop, Vue} from "vue-property-decorator";
  @Component
  export default class ListChat extends Vue{
        @Prop() typeView!: number
        @Prop({required: true}) readonly name!: string
    }
</script>

<style scoped>

</style>
