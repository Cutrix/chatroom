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
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
              <list-chat :type-view="typeView" name="Landry" @open-chat="openSimpleChat"></list-chat>
            </div>

          </div>

            <div class="row">
              <chat :id-user="1" name="Houessinon" @add-member="choiceMember"/>
              <!--<chat :id-user="2" name="Laura" @add-member="choiceMember"/>-->


            </div>


        </div>
          <!--<chat :id-user="1" name="Houessinon"/>-->
          <!--<chat :id-user="2" name="Laura"/>-->
          <!--<chat :id-user="3" name="Konan"/>-->


      </div>

    </div>
  </div>
</template>

<script lang="ts">
  import {Component, Vue} from "vue-property-decorator";
  import Chat from "@/components/Chat.vue"
  import ListChat from "@/components/ListChat.vue";
  import ChatItem from "@/components/ChatItem.vue";
  import VEmojiPicker from 'v-emoji-picker';

  @Component({
      components: {
        ListChat, Chat, ChatItem, VEmojiPicker
      }
    })
    export default class Home extends Vue {
        constructor() {
          super();
          this.show = true
          this.showBoxChat = true
          this.showChat = false
          this.typeView = 0
          this.isMinimize = false
          this.min = false
        }

        private show: boolean
        private showBoxChat: boolean
        private showChat: boolean
        private typeView: number
        private minimizeThis!: number
        private isMinimize: boolean
        private min: boolean

        public openBoxChat(): void {
          this.showBoxChat = false
          this.showChat = true
        }

        public changeView(view: number): void {
          this.typeView = view
        }

        public openSimpleChat(): void {
          this.showChat = true
          this.showBoxChat = true
        }

        public minimize(): void {
          this.isMinimize = !this.isMinimize
        }

        public selectEmoji(emoji: object): void {
          console.log(emoji)
        }

        public doMinimize(): void {
          this.min = !this.min
        }

        public choiceMember(): void {
          this.showBoxChat = false
        }
    }
</script>

<style scoped>
  .outer {background-color:lightgray;}
  .outer > * {
    display:inline-block;
    background-color:lightgreen;
  }

  .one {width:80px; height:80px;}
  .two {width:80px; height:80px;}
  .three {width:80px; height:100px;}

</style>
