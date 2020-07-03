<template>
  <div class="row">
    <!-- Bar en haut du chat -->
    <!-- TODO au clic de la souris sur cette box la elle doit se replier -->
    <div class="col-md-11 ml-4 px-0" @click="replier" style="cursor:pointer;">
      <span class="text-black-50"><i class="fa fa-user fa-2x"></i></span>
      <span class="text-black-50 h5 pl-5">{{ name }}</span>
      <div class="float-right pt-2 px-3">
        <span class="text-black-50 h5 pr-3"><i class="fa fa-plus"></i></span>
        <span class="text-black-50 h5 pr-3"><i class="fa fa-cog"></i></span>
        <span class="text-black-50 h5"><i class="fa fa-close"></i></span>
      </div>
    </div>

    <div class="col-md-9 pt-3 ml-1">
      <input type="search" class="form-control" placeholder="Rechercher">
    </div>

    <div class="col-md-2 pt-3">
      <span><i class="fa fa-search pt-2 text-black-50"></i></span>
    </div>

    <!-- insertion des differents elements du chat -->

    <chat-item :msg="item.msg" :list-user-conversation="idUser" v-for="(item, index) in itemsChatItems" :key="index"/>
    <!--<chat-item is-other="false" msg="Comment tu vas ?" :list-user-conversation="idUser"/>-->

    <!-- le champ textuel pour les reponses -->

    <textarea name="" id="" cols="45" rows="3" class="ml-4 mt-3" placeholder="Repondre"></textarea>

    <!-- Ici les differents bouton pour provoquer en duel -->
    <div class="col-md-11">
      <span><i class="fa fa-close"></i></span>
    </div>
  </div>
</template>

<script lang="ts">
  import {Component, Prop, Vue} from "vue-property-decorator"
  import ChatItem from "@/components/ChatItem.vue"

  @Component({
    components: {
      ChatItem
    }
  })
  export default class Chat extends Vue{
    @Prop({required: true}) idUser!: number
    @Prop({required: true}) readonly name!: string
    //private itemsChatItems: Array<string> = ['Salut', 'Comment tu vas ?']
    private itemsChatItems: Array<object> = [{other: false, msg: 'Salut'}, {other: true, msg: 'Comment tu vas ?'}]

    public replier(): void {
      const payload = {name: this.name, chat: this.itemsChatItems}
      this.$emit('replier-chat', payload)
    }
  }
</script>

<style scoped>

</style>
