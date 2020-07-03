<template>
  <div>
    <div class="container">
      <div class="row mt-5" style="border: 1px solid white; box-shadow: 0px 1px 5px 1px rgba(0,0,0,1);">
        <div class="col-md-12" style="width: 100%">
          <h2><i class="fa fa-close"></i> VOTRE <span class="text-white">DUEL</span> AVEC <span class="text-white">FRANKLIN</span></h2>
        </div>
      </div>

      <!-- Bouton sur le coin pour afficher la box de chat  -->
      <div class="row">
        <div class="col-md-12 fixed-bottom">
          <div class="float-right py-2 text-center text-warning bg-white" style=" width: 5%;" v-show="show" @click="openBoxChat">
            <span><i class="fa fa-user"></i></span>
            <span class="badge badge-pill badge-warning">1</span>
          </div>

          <!-- box pour la discussion -->
          <div class="float-right py-2 text-warning bg-white" style=" width: 40%;" v-show="!showBoxChat">
            <div class="col-md-12">
              <span><i class="fa fa-user text-black-50"></i></span>
              <div class="dropdown float-right text-right">
                <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                  <i class="fa fa-cog"></i>
                </button>
                <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
                  <button class="dropdown-item" @click="changeView(1)">Liste</button>
                  <button class="dropdown-item" @click="changeView(0)">Galerie</button>
                </div>
              </div>
            </div>
            <!-- Rechercher un ami -->
            <div class="col-md-12">
              <input type="search" class="form-control" placeholder="Rechercher un ami">
            </div>
            <!-- Les personnes connecte -->

            <div :class="{row: !typeView}" style="height: 500px; overflow: scroll" class="p-3">
              <list-chat :type-view="typeView" name="Papou" @open-chat="openSimpleChat"></list-chat>
            </div>

          </div>

          <!-- Conversations -->
          <div class="float-right py-2 text-warning bg-white" style="width: 30%; box-shadow: 0px 0px 7px 0px rgba(0,0,0,0.75);" v-show="showChat">
            <!-- papa -->
            <!--<chat @replier-chat="reduire" name="Papou" :id-user="1"/>-->
            <!--<chat @replier-chat="reduire" name="Paouney" :id-user="2"/>-->
          </div>


          <div style="width: 70%;">
            <!--<div class="col-md-3 float-right bg-white mx-2" style="border: 2px solid yellow">
              <span><i class="fa fa-user"></i></span>
              <span class="pl-4">Jessica</span>
              <div class="float-right">
                 <span><i class="fa fa-plus pr-2"></i></span>
                 <span><i class="fa fa-cog pr-2"></i></span>
                 <span><i class="fa fa-close"></i></span>
              </div>
            </div>-->


            <!--<div class="col-md-3 float-right bg-white mx-2" style="border: 2px solid yellow">
              <span><i class="fa fa-user"></i></span>
              <span class="pl-4">Jessica</span>
              <div class="float-right">
                <span><i class="fa fa-plus pr-2"></i></span>
                <span><i class="fa fa-cog pr-2"></i></span>
                <span><i class="fa fa-close"></i></span>
              </div>
            </div>-->

            <min-chat @close="close" :data="itemsMinChatConversation" :id="1" @delete-min-chat="delMinChat" v-show="itemsMinChatConversation !== {}"/>
            <min-chat @close="close" :data="itemsMinChatConversation" :id="2" @delete-min-chat="delMinChat" v-show="itemsMinChatConversation !== {}"/>
            <min-chat @close="close" :data="itemsMinChatConversation" :id="3" @delete-min-chat="delMinChat" v-show="itemsMinChatConversation !== {}"/>

          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script lang="ts">
  import {Component, Vue} from "vue-property-decorator";
  import Chat from "@/components/Chat.vue"
  import ListChat from "@/components/ListChat.vue";
  import MinChat from "@/components/MinChat.vue";

  @Component({
      components: {
        ListChat, Chat, MinChat
      }
    })
    export default class Home extends Vue {
        constructor() {
          super();
          this.show = true
          this.showBoxChat = true
          this.showChat = false
          this.typeView = 0
          this.itemsMinChatConversation = []
        }

        private show: boolean
        private showBoxChat: boolean
        private showChat: boolean
        private typeView: number
        private itemsMinChat: Array<string> = ['Jessica', 'Mona']
        private itemsMinChatConversation: Array<object>

        public openBoxChat(): void {
          this.showBoxChat = false
          this.show = false
        }

        public changeView(view: number): void {
          this.typeView = view
        }

        public openSimpleChat(): void {
          this.showChat = true
          this.showBoxChat = true
        }

        public reduire(data: Array<object>): void {
          this.itemsMinChatConversation = data
          this.showChat = false
        }

        public close(id: number): void {
          this.itemsMinChat.splice(id, 1)
        }

        public delMinChat(): void {
          console.log(this.itemsMinChatConversation)
        }
    }
</script>

<style scoped>
</style>
