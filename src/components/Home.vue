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
            <!--<div class="row">
              <div class="col-md-3 text-center text-black-50 mt-3 ml-3" style="border-bottom: 3px solid green; height: 20%">
                <span><i class="fa fa-user fa-2x"></i></span>
                <h6>Houessi</h6>
              </div>

              <div class="col-md-3 text-center text-black-50 mt-3 ml-3" style="border-bottom: 3px solid orange; height: 20%">
                <span><i class="fa fa-user fa-2x"></i></span>
                <h6>Houessi</h6>
              </div>

              <div class="col-md-3 text-center text-black-50 mt-3 ml-3" style="border-bottom: 3px solid green; height: 20%">
                <span><i class="fa fa-user fa-2x"></i></span>
                <h6>Houessi</h6>
              </div>

              <div class="col-md-3 text-center text-black-50 mt-3 ml-3" style="border-bottom: 3px solid orange; height: 20%">
                <span><i class="fa fa-user fa-2x"></i></span>
                <h6>Houessi</h6>
              </div>
            </div>-->
            <!--<div class="row">
              <div class="col-md-11 ml-4 mr-4 mt-3" style="border-bottom: 2px solid black">
                <span><i class="fa fa-user fa-2x text-black-50"></i></span>
                <span class="pl-5 text-black-50 h5">sqdsqqds</span>
                <span class="badge badge-pill badge-warning float-right p-2">1</span>
              </div>

              <div class="col-md-11 ml-4 mr-4 mt-3" style="border-bottom: 2px solid black">
                <span><i class="fa fa-user fa-2x text-black-50"></i></span>
                <span class="pl-5 text-black-50 h5">sqdsqqds</span>
                <span class="badge badge-pill badge-warning float-right p-2">1</span>
              </div>

              <div class="col-md-11 ml-4 mr-4 mt-3" style="border-bottom: 2px solid black">
                <span><i class="fa fa-user fa-2x text-black-50"></i></span>
                <span class="pl-5 text-black-50 h5">sqdsqqds</span>
                <span class="badge badge-pill badge-warning float-right p-2">1</span>
              </div>

              <div class="col-md-11 ml-4 mr-4 mt-3" style="border-bottom: 2px solid black">
                <span><i class="fa fa-user fa-2x text-black-50"></i></span>
                <span class="pl-5 text-black-50 h5">sqdsqqds</span>
                <span class="badge badge-pill badge-warning float-right p-2">1</span>
              </div>

              <div class="col-md-11 ml-4 mr-4 mt-3" style="border-bottom: 2px solid black">
                <span><i class="fa fa-user fa-2x text-black-50"></i></span>
                <span class="pl-5 text-black-50 h5">sqdsqqds</span>
                <span class="badge badge-pill badge-warning float-right p-2">1</span>
              </div>

              <div class="col-md-11 ml-4 mr-4 mt-3" style="border-bottom: 2px solid black">
                <span><i class="fa fa-user fa-2x text-black-50"></i></span>
                <span class="pl-5 text-black-50 h5">sqdsqqds</span>
                <span class="badge badge-pill badge-warning float-right p-2">1</span>
              </div>
            </div>-->

            <div :class="{row: !typeView}" style="height: 500px; overflow: scroll" class="p-3">
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
              <list-chat :type-view="typeView" name="Papou"></list-chat>
            </div>

          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script lang="ts">
  import {Component, Vue} from "vue-property-decorator";
  import ListChat from "@/components/ListChat.vue";

  @Component({
      components: {
        ListChat
      }
    })
    export default class Home extends Vue {
        constructor() {
          super();
          this.show = true
          this.showBoxChat = true
          this.typeView = 0
        }

        private show: boolean
        private showBoxChat: boolean
        private typeView: number
        public openBoxChat(): void {
          this.showBoxChat = false
          this.show = false
        }

        public changeView(view: number): void {
          this.typeView = view
        }
    }
</script>

<style scoped>

</style>
