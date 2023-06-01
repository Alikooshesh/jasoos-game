<script>
export default {
    props: {
        messageList: []
    },
    data() {
        return {
            playerIndex: 0,
            showCharacter: false
        }
    },
    methods: {
        changeDisplayWord(){
            if(this.showCharacter){
                if(this.playerIndex > this.messageList.length){
                    this.playerIndex = this.playerIndex + 1
                }

                this.showCharacter = !this.showCharacter
            }else{
                this.showCharacter = !this.showCharacter 
            }
        }
    },
    watch : {
        showCharacter(){
        console.log(this.showCharacter)
    }
  },
}
</script>

<template>
    <div class="w-full flex flex-col items-center gap-[16px]">
        <p>
            شما نفر
            {{ playerIndex + 1 }}
            از
            {{ messageList.length }}
            بازیکن هستید.
        </p>

        <div v-if="showCharacter">
            <h2 class="my-[16px]">
                شما یک
                {{ messageList[playerIndex].split("").some(item => item === "*") ? "جاسوس" : "شهروند" }}
                هستید
            </h2>

            <h4>
                کلمه :‌
                {{ messageList[playerIndex] }}
            </h4>
        </div>

        <p v-else>برای نمایش کاراکتر و کلمه دکمه پایین را کلیک کنید.</p>

        <button 
            @click="changeDisplayWord()" 
            class="max-w-[250px] py-[8px] px-[16px] rounded-[10px] bg-red-600 text-white">
            {{ showCharacter ? "مخفی کردن کلمه" : "نمایش کلمه" }}
        </button>
    </div>
</template>