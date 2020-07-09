<template>
  <div class="row">
    <div class="col-md-3 ml-3 px-2">
      <span class="text-black-50 pt-5"><b>11:14</b></span>
    </div>

    <div style="word-wrap: break-word;">
      <span :style="colorOther">{{ msg }}</span>
    </div>

    <div style="word-wrap: break-word;" v-if="patner">
      <span style="color: green">{{ msg }}</span>
    </div>
  </div>

</template>

<script lang="ts">
    import { Vue, Component, Prop } from "vue-property-decorator";

    @Component
    export default class ChatItem extends Vue{

        constructor() {
          super();
          this.colorPatner = 'color: green'
          this.patner = false;
        }

        @Prop({default: false}) isOther!: boolean
        @Prop() readonly msg!: string
        @Prop({default: 'color: black'}) readonly color!: string
        private colorOther: string = (this.isOther) ? 'color: orange' : 'color: black';
        private colorPatner: string;
        private patner: boolean
    }
</script>

<style scoped>

</style>
