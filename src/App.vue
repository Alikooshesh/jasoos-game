<script>
import {words} from './static_data/words'
import GameDataForm from './components/GameDataForm.vue';
export default{
  components : {
    GameDataForm
  },
  data(){
    return {
      words,
      gameStep : 0,
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
        this.gameStep = 1
      }
    }
  }
}
</script>

<template>
  <GameDataForm :setGameData="setGameData"/>
</template>