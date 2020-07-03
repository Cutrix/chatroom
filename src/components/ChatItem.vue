<template>
  <div class="row" style="width: 100%">
    <div class="col-md-2 ml-3 px-2">
      <span class="text-black-50 pt-2"><b>11:14</b></span>
    </div>

    <div style="word-wrap: break-word;">
      <span :style="colorOther" style="padding-right: 15px">{{ msg }}</span>
    </div>
  </div>

</template>

<script lang="ts">
    import { Vue, Component, Prop } from "vue-property-decorator";

    @Component
    export default class ChatItem extends Vue{
        @Prop({default: false}) isOther!: boolean
        @Prop() readonly msg!: string
        private colorOther: string = (this.isOther) ? 'color: orange' : 'color: black';
    }
</script>

<style scoped>

</style>
