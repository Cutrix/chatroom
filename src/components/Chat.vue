<template>
    <div class="col-md-3 bg-white mx-3 py-1">
      <div v-show="hasPatner" style="box-shadow: 0px 0px 7px -1px rgba(0,0,0,0.75);" @click="addFriend">
        <list-chat name="landry"></list-chat>
      </div>

      <div style="cursor:pointer;" @click="minimizise">
        <span><i class="fa fa-user pr-4"></i></span>
        <span>{{ name }}</span>
        <div class="float-right" style="clear: both">
          <span @click="addMember"><i class="fa fa-plus pr-2"></i></span>
          <b-dropdown html="<span><i class='fa fa-cog pr-2'></i></span>" no-caret variant="default">
            <b-dropdown-item>Supprimer la conversation</b-dropdown-item>
            <b-dropdown-item>Ignorer les messages</b-dropdown-item>
            <b-dropdown-item>Bloquer les messages</b-dropdown-item>
          </b-dropdown>
          <span><i class="fa fa-close"></i></span>
        </div>
      </div>

      <!--pour ajouter un nouveau partenaire -->
      <div style="cursor:pointer;" @click="minimizise" v-show="newPatner">
        <span><i class="fa fa-user pr-4"></i></span>
        <span>{{ name }}</span>
      </div>

      <div v-if="minimize" :style="min" class="pt-3">
        <chat-item msg="Esai un"/>
        <chat-item msg="Lequel ?" :is-other="true"/>

        <b-dd-divider></b-dd-divider>

        <div v-if="hasPatner">
          <chat-item msg="je suis de parler a nouveau" :patner="true"></chat-item>
        </div>

        <!--<textarea name="" id="" cols="20" rows="1" placeholder="Repondre..." v-model="reponse">
      </textarea>-->
        <b-form-textarea
          id="textarea"
          v-model="reponse"
          placeholder="Repondre..."
          rows="3"
          max-rows="6"
        ></b-form-textarea>
        <div class="col-md-12">
          <img src="../assets/battle1.png" alt="icone_battle">
          <!--<i class="fa fa-user float-right py-0" @click="activeEmoji" style="cursor: pointer"></i>-->
          <span class="float-right"><img src="../assets/smile.svg" alt="smile" @click="activeEmoji" style="cursor: pointer" width="32" height="32"></span>
        </div>
        <VEmojiPicker @select="selectEmoji" v-show="showEmoji"/>
      </div>
    </div>

</template>

<script lang="ts">
  import {Component, Prop, Vue} from "vue-property-decorator"
  import ChatItem from "@/components/ChatItem.vue"
  import ListChat from "@/components/ListChat.vue";
  import VEmojiPicker from 'v-emoji-picker';

  @Component({
    components: {
      ChatItem, VEmojiPicker, ListChat
    }
  })
  export default class Chat extends Vue{

    constructor() {
      super();
      this.minimize = false
      this.showEmoji = false
      this.reponse = ""
      this.hasPatner = false
      this.newPatner = false
    }

    @Prop({required: true}) idUser!: number
    @Prop({required: true}) readonly name!: string
    @Prop() readonly toMinimize!: number
    @Prop({default: false}) isMinimize!: boolean
    private minimize: boolean
    private showEmoji: boolean;
    private reponse: string
    private hasPatner: boolean
    private newPatner: boolean

    public minimizise(): void {
      this.minimize = !this.minimize
    }

    public selectEmoji(emoji: any): void {
      this.reponse += JSON.stringify(emoji.data).split('"').join('');
    }

    public activeEmoji(): void {
      this.showEmoji = !this.showEmoji
    }

    public addMember(): void {
      this.hasPatner = true
    }

    public addFriend(): void {
      this.newPatner = true
      this.hasPatner = false
    }

    get min() {
      if (this.isMinimize) return 'display: none'
      else return 'display: block'
    }
  }
</script>

<style scoped>

</style>
