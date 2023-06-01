<script>
import {words} from './static_data/words'
import GameDataForm from './components/GameDataForm.vue';
import CharacterCard from './components/CharacterCard.vue';

export default{
  components : {
    GameDataForm,
    CharacterCard
  },
  data(){
    return {
      words,
      gameStep : false,
      gameData : {
        playerCount : null,
        spyCount : null,
        selectedWord : null,
        messageList : []
      }
    }
  },
  watch : {
    gameStep(){
      console.log(this.gameData)
    }
  },
  methods:{
    setGameData(playerCount , spyCount){
      if(playerCount && spyCount){
        const tempWord = this.words[Math.floor(Math.random()*this.words.length)];

        this.playerCount = playerCount
        this.spyCount = spyCount
        this.selectedWord = tempWord

        const tempMessageList = []

        for(let i = 0;i < playerCount ; i++){
          tempMessageList.push(tempWord.word)
        }

        for(let i = 0;i < spyCount ; i++){
          tempMessageList[Math.floor(Math.random()*tempMessageList.length)] = "****"
        }
        this.gameData.messageList = tempMessageList
        this.gameStep = true
      }
    }
  }
}
</script>

<template>
  <div class="container mx-auto py-[24px]">
    <CharacterCard v-if="Boolean(gameStep)"  :messageList="gameData.messageList"/>
    <GameDataForm v-else="Boolean(gameStep)" :setGameData="setGameData"/>
    
  </div>
</template>