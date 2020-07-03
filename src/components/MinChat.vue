<template>
  <div class="col-md-3 float-right bg-white mx-2">
    <span><i class="fa fa-user"></i></span>
    <span class="pl-4">{{ data.name }}</span>
    <div class="float-right">
      <span @click="minimize = !minimize"><i class="fa fa-minus pr-2"></i></span>
      <span><i class="fa fa-plus pr-2"></i></span>
      <span><i class="fa fa-cog pr-2"></i></span>
      <span><i class="fa fa-close" @click="deleteMinChat"></i></span>
    </div>

    <div style="width: 100%; padding-top: 5px" v-show="minimize">
      <p v-for="(item, index) in data.chat" :key="index" :style="{color: colors[item.other]}">{{ item.msg }}</p>
    </div>
  </div>
</template>

<script lang="ts">
  import {Component, Prop, Vue} from "vue-property-decorator";

  @Component
  export default class MinChat extends Vue{

    constructor() {
      super();
      this.minimize = false
    }

    @Prop({required: true}) readonly id!: number
    @Prop({required: true}) readonly data!: object
    private colors: object = {true: 'orange', false: 'black'}
    private minimize: boolean

    public deleteMinChat(): void {
      this.$emit('delete-min-chat', this.id)
    }
  }
</script>

<style scoped>

</style>
